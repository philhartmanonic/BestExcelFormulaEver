# The best excel formula ever made
This is from a project where I needed to build a reporting tool in excel to show results and crosstabs from survey data.
The formula itself is just a small fraction of the work, as it involved creating a pseudo-database within Excel, and several other insane formulas.
But this formula is the coup de grace. 

If you're an Excel nerd - enjoy:
=IF(
AND(
$C$2=0,$D$1="P",$C17<>""),
SUMIF(
INDIRECT(
"Data!"&$B17&"2"):
INDIRECT(
"Data!"&$B17&"589"),
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!$C17,IF(
'Many to Many'!$B$2:$B$423=Results!$C$1,'Many to Many'!$C$2:$C$423),0)
),
weight)
/SUMIF(
INDIRECT(
"Data!"&$B17&"2"):
INDIRECT(
"Data!"&$B17&"589"),
"<>"&"NA",weight),
IF(
AND(
$C$2=0,$D$1="A",$C17<>""),
SUMPRODUCT(
INDIRECT(
"Data!"&$B17&"2"):
INDIRECT(
"Data!"&$B17&"589"),
weight)
/SUM(
weight),
IF(
AND(
$D$1="R",$C$2=0,$C17<>""),
SUMIF(
INDIRECT(
"Data!"&$B17&"2")
:INDIRECT(
"Data!"&$B17&"589"),
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!$C17,IF(
'Many to Many'!$B$2:$B$423=Results!$C$1,'Many to Many'!$C$2:$C$423),
0)
),
weight)
/SUM(
weight),
IF(
AND(
OR(
$E$1="P",$E$1="R1",$E$1="R2",$E$1="R3"),
$C17<>""),
SUMIFS(
weight,INDIRECT(
"Data!"&$B17&"2"):
INDIRECT(
"Data!"&$B17&"589"),
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!$C17,IF(
'Many to Many'!$B$2:$B$423=Results!$C$1,'Many to Many'!$C$2:$C$423),
0)
),
INDIRECT(
"Data!"&Results!AB$5&"2"):
INDIRECT(
"Data!"&Results!AB$5&"589"),
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!AB$4,IF(
'Many to Many'!$B$2:$B$423=Results!$C$2,'Many to Many'!$C$2:$C$423),
0)
)
)/
SUM(
weight),
IF(
AND(
$E$1="A1",$C17<>"",AB$5<>""),
SUMPRODUCT(
IF(
INDIRECT(
"Data!"&AB$5&"2"):
INDIRECT(
"Data!"&AB$5&"589")=
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!AB$4,IF(
'Many to Many'!$B$2:$B$423=Results!$C$2,'Many to Many'!$C$2:$C$423),
0)
),
INDIRECT(
"Data!"&Results!$B17&"2"):
INDIRECT(
"Data!"&Results!$B17&"589")/
SUMIF(
INDIRECT(
"Data!"&AB$5&"2"):
INDIRECT(
"Data!"&AB$5&"589"),
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!AB$4,IF(
'Many to Many'!$B$2:$B$423=Results!$C$2,'Many to Many'!$C$2:$C$423),
0)
),
weight)
)
),
IF(
AND(
$E$1="A2",$C17<>"",AB$5<>""),
SUMPRODUCT(
IF(
INDIRECT(
"Data!"&$B17&"2"):
INDIRECT(
"Data!"&$B17&"589")=
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!$C17,IF(
'Many to Many'!$B$2:$B$423=Results!$C$1,'Many to Many'!$C$2:$C$423),
0)
),
INDIRECT(
"Data!"&Results!AB$5&"2"):
INDIRECT(
"Data!"&Results!AB$5&"589")/
SUMIF(
INDIRECT(
"Data!"&$B17&"2"):
INDIRECT(
"Data!"&$B17&"589"),
INDEX(
'Many to Many'!$F$2:$F$423,MATCH(
Results!$C17,IF(
'Many to Many'!$B$2:$B$423=Results!$C$1,'Many to Many'!$C$2:$C$423),
0),
weight)
)
)),
IF(
$E$1="A3","InvalidMatch","")
)
)
)
))
)
