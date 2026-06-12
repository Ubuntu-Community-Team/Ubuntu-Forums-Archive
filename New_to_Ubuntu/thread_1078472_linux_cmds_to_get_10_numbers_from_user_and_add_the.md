---
title: "linux cmds to get 10 numbers from user and add them"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-23
how to do this using linux commnds ??

I want to get 10 numbers from user

and to find their sum.....

i need it like this 

enter num1 [i must enter number here]
enter num2 
enter num3


and after 10 num, it must display the sum

---

### Post by davideotape on 2009-02-23
I don't think that you would be able to do this using shell scripts. I think you would have to run a program to do it for you.

---

### Post by matteojg on 2009-02-23
```

#! /bin/bash
declare -i sum

for (( i = 1 ; i < 11 ; i++ ))
 do
  echo "Please enter number $i"
  read input
  sum="$sum + $input"
 done
echo $sum
 
```

---

### Post by kimikrishna on 2009-03-01
thanks,..

i heard of some self excuting file called shelling scripting

how do i add this codes to that ?

---

### Post by Nepherte on 2009-03-01
Just paste it in a text file, give it a name and you're done. The line
```
#!/bin/bash
```
indicates it's is a bash shell script. To run it, make the file executable and run it in a terminal.

---

### Post by asmoore82 on 2009-03-01
If graphics are available, you might want to check out the "zenity" package -
included with Ubuntu desktop editions by default;
see ```
man zenity
```

My version of Your solution...
file: sum
```
#!/bin/bash

sum="0"

for x in 1st 2nd 3rd 4th 5th 6th 7th 8th 9th 10th
do
	num=`zenity --scale --title "Enter A Number" --min-value 1 --max-value 99 \
		--text "Please, select your ${x} number." --value 50`
	sum="$(( sum + num ))"
done

zenity --info --title "Grand Total" --text "The Sum is:\n  $sum"

#End of File
```

to make it executable: ```
chmod +x */path/to/file/sum*
```

to run it: ```
*/path/to/file/sum*
```
if the script is in your Working Directory, you will still have to tell
the shell the "path" to find it: a single dot meaning "THIS Directory" -
because more than likely, your current directory
is no in your global "PATH" for executables ... ```
./sum
```

Notes: shells weren't really designed with arithmetic in mind;
So...

notice the quotation in the simple assignment statement sum="0" -
becase as far as the shell is concerned the 0 character is just text.

notice the use of the "$(( ... ))" construct to force the shell to do
C-style arithmetic - and that's not a mistake inside of it - you don't have a to
reference variables with the `$` character inside the "$(( ... ))" construct

:KS

---

