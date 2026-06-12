---
title: "Weird bash scripting problem"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by ukyo_rulz on 2011-07-16
Hello there. I am trying to write a script that will get specific tracks from an mkv file. Let's say it's the sound track. I've gotten it working to the point that I have these three variables:

$BASENAME -> filename of the mkv file
$TRACKNO -> TID of the track
$NEWNAME -> name for the output

My problem is when I try to $TRACKNO to the final command. If I do something like this it works:

```
mkvextract tracks "$BASENAME.mkv" 2:"$NEWNAME"
```

But this does not work:
```

mkvextract tracks "$BASENAME.mkv" "$TRACKNO":"$NEWNAME"
```

I get this error (assuming TRACKNO is 2):
```

Error: Invalid track ID/file name specification in argument ' 2:output.ac3'.
```

What's even more infuriating is that I can actually echo the above command and past it to the command line... and it works! I have no idea why it refuses to work within the script.

---

### Post by cipherboy_loc on 2011-07-16
Does the following line work?

```

mkvextract tracks "$BASENAME.mkv" "$TRACKNO:$NEWNAME"

```

I suspect it is that the double quotes are getting passed to the program as arguments. Hence, rather than seeing 2:<contents of $NEWNAME>, it sees "2":"<contents of $NEWNAME>", which would display properly as 2:<contents of $NEWNAME> when echoed.


Cipherboy

---

### Post by ukyo_rulz on 2011-07-16
Unfortunately I still get the same problem. Perhaps it's an issue with how I get TRACKNO? It's a bit of a hack because I'm not really a scripting expert:

```
     MKVINFO=`mkvinfo "$MKVFILE"`
     NOTFOUND=true
     while read -r line
     do
          if $NOTFOUND ; then
               if echo "$line" | grep -q "Track type: audio" ; then
                    NOTFOUND=false
               fi

               if echo "$line" | grep -q "Track number:" ; then
                    IFS=":"
                    for x in $line
                    do
                         TRACKNO=`echo $x`
                    done
               fi
          fi
     done <<< $MKVINFO
```

---

### Post by idoitprone on 2011-07-17
```
 if $NOTFOUND ; then
```

well since you programming bash, you if else clause looks wrong, you need brackets
I not sure if
```
if [ $NOTFOUND ]; then
``` 
works
look at ```
man test
```

[http://tldp.org/LDP/abs/html/nestedifthen.html](http://tldp.org/LDP/abs/html/nestedifthen.html)

---

### Post by ukyo_rulz on 2011-07-17
> **idoitprone said:**
> well since you programming bash, you if else clause looks wrong, you need brackets


Not sure what the brackets are supposed to do, since I've seen many examples online that don't have them. The if clause seems to work fine anyway, since it gets the correct track number every time. I tried putting brackets on it but it just broke the script and I got this error:


```
./testscript: line 40: [true]: command not found
```

---

### Post by idoitprone on 2011-07-17
> **ukyo_rulz said:**
> Not sure what the brackets are supposed to do, since I've seen many examples online that don't have them. The if clause seems to work fine anyway, since it gets the correct track number every time. I tried putting brackets on it but it just broke the script and I got this error:


```
./testscript: line 40: [true]: command not found
```

  opps my bad i just realize what you have done is perfectly valid. I was wrong doodddood. I am trying to find other errors

---

### Post by idoitprone on 2011-07-17
```
echo $MKVINFO | while read -r line
```      i believe read line recieve info from standard output or input, which means you have to pipe it

---

### Post by ukyo_rulz on 2011-07-17
I figured out my problem. Basically I didn't have confidence in my ability to use sed or tr or awk, so I hacked IFS to another value and used a for loop to tokenize the mkvinfo string:

```
               if echo "$line" | grep -q "Track number:" ; then
                    IFS=":"
                    for x in $line
                    do
                         TRACKNO=`echo $x`
                    done
               fi
```

The problem is I forgot to change it back. Adding this statement fixed the problem:

```
unset IFS
```

---

### Post by ukyo_rulz on 2011-07-17
Hooooookay I *thought* I fixed the problem by unsetting IFS, but that only made the script work for files that don't have spaces in the filename. The script broke when I tried to use it on filenames with spaces. So I finally came up with this super dirty hack to get it running.

First, put the commands in a text file:

```
echo "mkvextract tracks \"${BASENAME}.mkv\" ${TRACKNO}:\"${NEWNAME}\"" >> commands.txt
```

Then, execute the text file

```
./commands.txt
```

The script is now ugly and inelegant as heck, but it works.

---

### Post by idoitprone on 2011-07-17
next time if you want help with a script

give us the test case
such as

remove all space from this sentence to periods
remove.all.space.from.this.sentence.to.periods

---

### Post by ukyo_rulz on 2011-07-18
Sorry, dude. I didn't actually realize that spaces would be a problem until after I started trying to use the script for real. My test case was just testfile.mkv so it wouldn't have helped to post it.

---

