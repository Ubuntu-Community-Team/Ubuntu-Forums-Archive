---
title: "kill both parent and child processes"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by flylehe on 2010-01-04
Hi,

I am running a bash script as a background job. The bash script calls a time-consuming executable. If I am not wrong, the running of the bash script is the parent process and the running of the executable is the child process.

(1) when I look at the output of top, it only shows the child process which is the running of the executable, not shows the parent process which is the running of the script. Just wonder why not show both? And how to show both?

(2) I now want to stop the whole running by killing the parent process which is the background job
```

kill -9 $(jobs -p)

```
The terminal shows that the running of the bash script is killed. But the running of the executable still hangs on the output of top. I just wonder how to kill both parent and child process?

Thanks and regards!

---

### Post by duanedesign on 2010-01-04
I found this script that kills all child processes for a given PID

```
# This script will kill all the child process id for a  given pid
#Store the current Process ID
CURPID=$$

# This is process id, parameter passed by user
ppid=$1

if [ -z $ppid ] ; then
   echo No PID given.
   exit;
fi

arraycounter=1
while true
do
        FORLOOP=FALSE
        # Get all the child process id
        for i in `ps -ef| awk '$3 == '$ppid' { print $2 }'`
        do
                if [ $i -ne $CURPID ] ; then
                        procid[$arraycounter]=$i
                        arraycounter=`expr $arraycounter + 1`
                        ppid=$i
                        FORLOOP=TRUE
                fi
        done
        if [ "$FORLOOP" = "FALSE" ] ; then
           arraycounter=`expr $arraycounter - 1`
           ## We want to kill child process id first and then parent id's
           while [ $arraycounter -ne 0 ]
           do
             kill -9 "${procid[$arraycounter]}" >/dev/null
             arraycounter=`expr $arraycounter - 1`
           done
         exit
        fi
done
## Kill Parent ID
kill -9 $CURPID
```

I would only use kill -9 as a last resort.
I usually start with:
```
kill PID
```
wait a few seconds
if it is still alive:
```
kill -2 PID
```
wait a few seconds
if it is still alive:
```
kill -1 PID
```
Now it should be dead and gone, but there is always the last, dirty resort:
```
kill -9 PID
```

Note, that kill -9 cuts the throat without giving the sick process any chance of cleaning up after itself (sockets/temp/children a.o.)

---

