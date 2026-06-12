---
title: "Some If coding curiousity"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by IrishLad on 2010-03-14
I was wondering something with this piece of code

```
if [ "$1" = "-ofilename" ] || [ "$1" = "--output=filename" ]; then
            echo "Output file: test2.txt"
        fi
```could I put multiple possible variables in with "$1" in case they are "-ofilename" as in like test "$2" "$3" etc. because I want to check if any of these are containing the correct value to make my IF true.

Cheers for any help its much appreciated. I have tried to research it but couldn't find anything that would help me.  Is this the correct section or should this be in programming? I put it here because its probably very simple if it can be done.

---

### Post by r-senior on 2010-03-14
My shell script is rusty so I won't quote any code but wouldn't the best approach be to iterate through all the supplied parameters, checking whether the first character is '-', then use a case statement to deal with the possibilities? Anything that doesn't begin with '-' is processed as a non-option parameter.

---

### Post by IrishLad on 2010-03-14
Thanks for the reply, I'm not sure your method is entirely suitible because I could have a number of different inputs and I was trying to think of how to code them so it didn't matter what order they were in.

-outfile
-n
-v
-V
etc

SO I was wondering could I put an OR statement in here, changing this

if [ "$1" = "-ofilename" ] 

to this 
if [ "$1" OR "$2" OR "$3" = "-ofilename" ] 

Id ya get what I mean

---

### Post by r-senior on 2010-03-14
Something like this ... but I'll repeat my disclaimer about my shell scripting being rusty.

```

#!/bin/bash

until [ -z "$1" ]
do
	if [[ "$1" == "-o" || "$1" == "--output-file" ]]; then
		shift
		if [ -z "$1" ]; then
			echo 'ERROR: Missing filename'
			exit
		fi
		echo 'Output file = '$1
	fi
	if [[ "$1" == "-v" || "$1" == "--verbose" ]]; then
		echo 'Verbose'
	fi
	shift
done
echo 'Do processing now, based on parameters ...'

```

Obviously you'd do something useful in the real script, rather than just echoing the parameters and their meanings. This script lets you use commands like:

$ ./myscript -v
$ ./myscript -v -o file.txt
$ ./myscript -o file.txt
$ ./myscript -o file.txt --verbose

and so on ...

---

### Post by Rocket2DMn on 2010-03-14
Bash stores command line arguments in an array "$@". You could loop through this array.  Here is an example of printing out the command line arguments:
```

#!/bin/bash
for i in $@
	do
		echo $i
	done

```

---

### Post by IrishLad on 2010-03-14
THanks for the Replies guys I'll try and implement some of it now cheers again ;)

---

