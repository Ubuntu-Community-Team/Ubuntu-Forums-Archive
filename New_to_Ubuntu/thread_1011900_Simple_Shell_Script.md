---
title: "Simple Shell Script"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by slibuntu on 2008-12-15
I'm writing a simple script to post to twitter, and I'm doing a check on the input to make sure there re less than 140 characters, I keep getting errors though

Here's the code

```
#!/bin/sh


x= echo $@ | wc -c
if [ $x -lt 140 ] then
curl -o curloutput --silent --basic --user "USERNAME:PASSWORD" --data-ascii "status=`echo $@|tr ' ' '+'`" "http://twitter.com/statuses/update.json" 
echo "Post Successful"
fi

if [ $x -gt 140 ] then
echo "Too many characters, maximum 140, try again."
fi
echo $@
```


There's no problem with the curl part, that works on its own.

I've been getting errors in relation to the if loop

Thanks for any help guys

---

### Post by Sarmacid on 2008-12-15
You're missing a ;

```
if [ $x -lt 140 ] ; then
```

But I'm still getting an error.
NVM
need to add backquotes to the variable
```
x=`echo $@ | wc -c`
```

---

### Post by slibuntu on 2008-12-15
I'm getting an error on the -gt aspect, it says its expecting a unary operator...hmmm

---

### Post by slibuntu on 2008-12-15
What do these error messages mean??
```

./twitter: line 6: [: -lt: unary operator expected
./twitter: line 11: [: -gt: unary operator expected

```

---

### Post by Sarmacid on 2008-12-15
Forgot to mention I used quotes :x
```
if [ "$x" -lt 140 ] ; then
```

---

### Post by slibuntu on 2008-12-15
```

x=`echo $@ | wc -c`
if [ $x -lt 140 ]; then
curl -o curloutput --silent --basic --user "USERNAME:PWD" --data-ascii "status=`echo $@|tr ' ' '+'`" "http://twitter.com/statuses/update.json"

echo "Post Successful"
fi

if [ $x -gt 140 ]; then
echo "Too many characters, maximum 140, try again."
fi
echo $@

```

works, for some reason.

---

### Post by LinuxPS2 on 2008-12-16
Cool, hrm, I wonder if you could use something like zenity to have a simple and easy gui for this, I haven't worked with zenity much but it seems pretty straight forward... 

Well thanks for the script - I might try to add the zenity frontend later - I have to take the last of my finals today... you might also be interested in a script I've been working on with twitter [http://ubuntuforums.org/showthread.php?t=1001225]("http://ubuntuforums.org/showthread.php?t=1001225")

Keep up the good work

[EDIT]
Ok, so I just made it with zenity real quick to see how it works - seems to do OK
```
#!/bin/bash

STATUS=$(zenity --entry --text "What are you doing?")
X=${#STATUS}

if
[ $X -lt 140 ];
then
curl -u EMAILADDRESS:PASSWORD -d status="$STATUS" http://twitter.com/statuses/update.xml


zenity --info --text "Post Successful"
fi

if
[ $X -gt 140 ];
then
zenity --error --text "Too many characters, maximum 140, try again."
fi
echo $@

exit
```

is there a way in the command line to create a file that will expire after a given amount of time and either delete itself or not read - that way you could make the script ask for usename and password but only every few hours or so instead of everytime... I guess one could just setup a cron job that erased the password file every so often but there has to be an easier way?... maybe get it to print the date and time on the password file and check it that way?... hrm...

---

