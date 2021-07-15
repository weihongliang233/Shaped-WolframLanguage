```mathematica
<< M2MD`
```

```mathematica
MDExport[NotebookDirectory[] <> "Tensor-Dimension-Engine.md", 
 EvaluationNotebook[]]

(*"G:\\GitHub Local \
Repository\\Shaped-WolframLanguage\\Tensor-Dimension-Engine.md"*)
```

```mathematica
Clear@"Global`*"
```

**类型运算**

```mathematica
Clear@Type
```

```mathematica
baseType =
 Type[Association[]]
```

```mathematica
func = Type[Association[
   "type" -> "function",
   "method" -> add,
   "checker" -> {checker}
   ]]
```

```mathematica
x = Type[Association[
   "type" -> "array",
   "properties" -> Association["length" -> 3]
   ]]
```

```mathematica
y = Type[Association[
   "type" -> "array",
   "properties" -> Association["length" -> 4]
   ]]
```

```mathematica
removeHead[x_[y_]] := y
```

```mathematica
add[x_Type, y_Type] :=
 Module[{number}, 
  number = Total[removeHead[#]["properties"]["length"] & /@ {x, y}];
  Type[Association[
    "type" -> "array",
    "properties" -> Association["length" -> number]
    ]]
  ]
```

```mathematica
checker[x_] := True
```

```mathematica
x_Type[y___Type] := ToExpression[removeHead[x]["method"]][y]
```

```mathematica
func[func[x, y], x]
```

```mathematica
func
```

```mathematica
x
```

```mathematica
y
```