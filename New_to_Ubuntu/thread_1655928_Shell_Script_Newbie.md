---
title: "Shell Script: Newbie"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by AlAK on 2010-12-30
Hi,
I am new to Linux, Ubuntu.  I was trying to find the maximum number of "#"'s in a line, for all lines in a file. I had written the following shell script. 

----------------------------------------------------------

 #!/bin/bash
cd /home/xyz/Desktop/
countnow=0
countmax=0
n=0
cat "test" | while read line
do 
countnow=$(echo "$line" | tr -cd "\#" | wc -m)
 if [ "$countnow" -gt "$countmax" ]
then countmax=$countnow
echo "Till line $n Max.Count is $countmax"
fi
n=$((n+1)) 
done 
echo "Overall Maximum is" $countmax
------------------------------------------------------------

Though I get the answer. The $countmax in the final echo gives an answer 0? It infact gives the same answer as what I set the variable to be in first2 lines. I think there is something to learn from this. Is it something about a global variable thing? Though thankfully the file I processed was small, in future, I might do something more complicated with this and would make mistakes because I missed the lesson here. Can you kindly point it out to me?

Thanks,

AK

---

### Post by georgemc on 2010-12-30
Ok – going to take a shot at this one.
 

 I think that when you pipe the output of “cat file” to your while loop, then the while loop is executed in a sub shell and when the loop is completed then the variables in that sub shell are not passed back to the main shell.
 

 If you change how the while loop reads file then the loop is executed within the main shell.
 

 ```

 #!/bin/bash
cd /home/xyz/Desktop/
countnow=0
countmax=0
n=0
  
# Remove the “cat” and the pipe and add a redirect at the end of the while loop

**while read line**
do 
    countnow=$(echo "$line" | tr -cd "\#" | wc -m)
    if [ "$countnow" -gt "$countmax" ]
        then countmax=$countnow
        echo "Till line $n Max.Count is $countmax"
    fi
    n=$((n+1))  
 
# add the redirect from your “test” file

**done  <  “test”**

echo "Overall Maximum is" $countmax
 
``` As a habit I tend not to use key words like “test” for file names or variables, some times you can get unexpected results within scripts.
 

 Hope this helps.
 George

---

### Post by blind2314 on 2010-12-30
Bah, george beat me to it!
 
He's right though. The way your script was written, a new "shell" was forked when executing it, and your modified countmax never made it back to its parent shell. Hence why you get 0 as your answer at the end. 
 
If you redirect the input a different way, like how george showed you, you'll get the correct answer.

---

### Post by AlAK on 2010-12-31
Thanks! I now understand.

btw cat test | while read line ->

Is one line "sent" to be read one at a time or cat test puts output in some buffer from where lines are read?

---

### Post by georgemc on 2010-12-31
Since every thing in *NIX is treated as a file, even stdin and stdout, there will be some sort of buffering done.
 

 Check out the “man stdio” and the “man read” pages, even though these are library functions all flavor of shells will use these functions.  “stdin” and “stdout” by default are line buffered only if they are not pointing to a device, something like a character device (/dev/s0 or /dev/tty).
 

 The buffer schema can be change within a program or script.  A whole other world to explore.  In bash scripts I usually never change the default behavior of stdin and stdout.  In “C” programs I do set stdin and stdout to the specific needs of that program, maybe block buffered or character oriented.
 

 It is my understanding that with “cat test | while read line” the read will pick one line from the buffer on each read.  From my observations looking at the process lists during a script execution, this is very subjective and only works with large files or some sort of user interaction, it appears to me that the “cat” process will hang around until the last line is flushed from the buffer by the read.
 

 To answer your question I would say: Yes “cat test” places its output into a buffer for the “read” to pick up one line at a time.
 

 George

---

