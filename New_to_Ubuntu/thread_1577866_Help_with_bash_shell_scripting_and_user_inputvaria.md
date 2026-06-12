---
title: "Help with bash shell scripting and user input/variables"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by chrisdazzo on 2010-09-19
:confused:

So I've been using bash for about three weeks now, and the 5-week elective class I'm taking at my university is really kicking my ***.

The assignment I've been struggling with for three days requires a script that does this when I enter a string or number as arguments with the script:
```

 % ./area
    usage: ./area <query> ...
    % ./area 303
    Area codes for "303":
       303 Central Colorado: Denver (see 970, also 720 overlay)
    % ./area 303 970
    Area codes for "303":
       303 Central Colorado: Denver (see 970, also 720 overlay)
    Area codes for "970":
       970 N and W Colorado (part of what used to be 303)
    % ./area Denver
    Area codes for "Denver":
       303 Central Colorado: Denver (see 970, also 720 overlay)
       720 Central Colorado: Denver (overlaid on 303)
    % ./area Wonderland
    Area codes for "Wonderland":
    % ./area enver
    Area codes for "enver":
       303 Central Colorado: Denver (see 970, also 720 overlay)
       720 Central Colorado: Denver (overlaid on 303)
    % ./area e
    Area codes for "e":
       there were 356 results (greater than 10)
```

Other things: can only use exp and grep. No perl, awk, or csh. And it has to be a bash script. And in all that, somehow, sort the output. 

Here's what I've pieced together so far, but the script just hangs when I invoke ./dazzo_area Denver 303 (for example). 

```

#! /bin/bash

search1 = $1
search2 = $2
search3 = $3
while [[ $# -le 3 ]]
do
   read $search1 && $search2 && $search3
   results = $search1 && $search2 && $search3
   echo grep $results -f ~cs155/pub/area-codes

if [[ $# -eq 0 ]]
then
   echo "Usage: $0 <search terms>"
   exit 1
fi

```

also,

```

#! /bin/bash

search=$(grep $1 && $2 && $3 -f  ~cs155/pub/area-codes)
let resultscount=$(grep $1 && $2 && $3 -c -f ~cs155/pub/area-codes)
statement=$(echo "Here are the results for your search:")

grep $1 && $2 && $3 -f ~cs155/pub/area-codes

if [[ $? -eq 0 ]]
then
${statement}${1},${2},${3}
echo $search

elif [[ $? -eq 0 && $resultscount -gt 10 ]]
then
echo $resultscount records found. Please narrow your search and try again.

elif [[ $resultscount -eq 0 ]]
then
echo Sorry, no matching results were found.

fi

```

I can't get either script to do anything. Help? Thanks in advance.
*And yes, I know how horrible this is, but I'd appreciate any help anyone could give me.*

---

### Post by bodhi.zazen on 2010-09-19
You are expected to do your own work / assignments, they are given for your learning.

I am sorry you are having problems, I suggest you ask your professor for guidance / advice.

---

