---
title: "Help with small bash script"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2010-12-11
All,

I am trying to create a small bash script which reads a file with 3 values per line.  I want to take those values and grep another file for them, if found, I want them to place that line in another file.

Ex:

Large file full of text (file.log)
Definitions File (values to grep for)

Line in definition file would look like:
email,pass

It loads that line and then creates a statement like:
cat file.log|grep email|grep pass >> acct.txt

Thanks in advance
Eric

---

### Post by low_rider on 2010-12-11
I'm still not quite clear on what the script is supposed to do, but from what it sounds like "awk" may be able to help.

---

### Post by Crusty Old Fart on 2010-12-12
Howdy Eric:

Not to be overly critical here, but scripting is somewhat of an exact science. Your post is a little short on specifics and kind of long on ambiguities.

Still, we can start with a sample script and then modify it as you reveal more detail regarding your requirements.

So, for a first shot at a solution, consider this:
```

#!/bin/bash
set -e

NUMLINES=$(cat def_file.txt | wc -l)

i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' def_file.txt)
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' def_file.txt)
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' def_file.txt)
  cat file.log | grep $VAL1 | grep $VAL2 | grep $VAL3 >> acct.txt
  i=$[$i+1]
done

exit 0

```A few questions came to mind as I was writing the script:

[LIST=1]
[*]You wrote that your definitions file had three values per line, but the example you used had only two: email,pass
[*]The example: email,pass indicates that the values are delimited by commas, but the code I wrote only works for parameters that are delimited by whitespaces. I need to know if your values are delimited by commas or whitespaces or if I should allow for both.
[/LIST]

---

### Post by J0hnnyBr@v0 on 2010-12-12
Crusty, 

First let me say thank you very much for this snippet of code.

I understand I didn't do the best job in explaining.  I am still trying to work out in my head what needs to be done.  I am no developer, and I have been writing a program to leverage Ettercap & SSL Strip for my pen testing.

The problem with the SSLStrip log file is it is usually large (79 MB text file)  and I have to go through it very carefully to find sets of credentials I've compromised.  So I have a definition file for all the different sites, such as facebook, gmail, etc.  The definition file is where the values come from.  I didn't include the first value, but it would be something like google.com or login.facebook.com


White space or comma, it doesn't matter it can be anything really.  The main thing is that it has to meet *all* 3 criteria to be written to the file.

So it should look for lines that have login.google.com & Email & Passwd and print that out...if it doesn't meet that reqirement it gets passed over.

I can provide you the files it you'd like...

Best Regards,
Eric

---

### Post by Crusty Old Fart on 2010-12-12
> **J0hnnyBr@v0 said:**
> Crusty, 

First let me say thank you very much for this snippet of code...

You're mighty welcome.

> 
White space or comma, it doesn't matter it can be anything really....

As long as there are no white spaces imbedded in any of the three values, it would be simplest to use white spaces as delimeters.
> The main thing is that it has to meet *all* 3 criteria to be written to the file. So it should look for lines that have login.google.com & Email & Passwd and print that out...if it doesn't meet that reqirement it gets passed over.


Yup...I picked up on that with the triple grep pipe instead of using the "-e" grep option three times. This line of code:
```

cat file.log | grep $VAL1 | grep $VAL2 | grep $VAL3 >> acct.txt 

```
will only write lines containing the values of _**ALL THREE**_ $VAL# parameters to the acct.txt file.
> 
 I can provide you the files it you'd like...

That would be very helpful. Even if you don't upload the entire SSLStrip log file, a good portion of it would go a long way to tweaking the script to get it exactly the way you want it.

Thanks in advance for providing the files.

Crusty

---

### Post by J0hnnyBr@v0 on 2010-12-12
Here's what the code looks like now and works like a charm!

#!/bin/bash

echo -n "Please enter the full path to your SSLStip Log file: "
read -e LOGPATH
#
echo -n "Please enter the full path to your definitions file: "
read -e DEFS
#
#!/bin/bash
set -e

NUMLINES=$(cat $DEFS | wc -l)

i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' $DEFS)
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' $DEFS)
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' $DEFS)
  cat $LOGPATH | grep $VAL1 | grep $VAL2 | grep $VAL3 >> /$PWD/accts.txt
  i=$[$i+1]
done

exit 0

Next step would be to take the output value of the variables only.

I've provided the files so you can see.  The output still have a ton of "junk" around it.  I can work with it the way it is, but do you think it could be cleaned up with some ease?

Also, here is a link to my program I will be adding it to.  It's very elementary.  Like I said...not a developer...but learning what I can.  Is there a way for me to put all the common stuff in one function...then call that function from my other functions?  Look at the code and you'll se what I mean.

[http://code.google.com/p/easy-creds/](http://code.google.com/p/easy-creds/)

---

### Post by J0hnnyBr@v0 on 2010-12-12
I've tested it a bit more agains the full sslstrip.log file and with a definitions file of more than 1 line and it doesn't seem to be working....

Not sure whats going on, but is it treating each line in the file as a separate set of valirables?

---

### Post by Crusty Old Fart on 2010-12-12
> **J0hnnyBr@v0 said:**
> I've tested it a bit more agains the full sslstrip.log file and with a definitions file of more than 1 line and it doesn't seem to be working....

Not sure whats going on, but is it treating each line in the file as a separate set of valirables?

Yes...it treats each line of the definitions file as a separate set of three variables. [COLOR=Red][s]My guess is that the grep pipeline is failing due to being special character intolerant.[/s][/COLOR] [COLOR=Blue]**Nope...the problem was "set -e" forcing an exit when the grep pipeline had a null result.**[/COLOR]

I'm taking a closer look at it and will post again soon.

---

### Post by J0hnnyBr@v0 on 2010-12-12
sounds good, again much appreciated!

when I grep the values against the file they come back fine.

ie: cat sslstrip.log|grep salesforce.com|grep username|grep pw

Returns everything exactly as expected, when run through the program, nothing is returned.  Not sure if that helps you at all.

Best Regards,
Eric

P.s.  I'll make sure you get a shoutout in the code for this help!!  It's currently being downloaded like hotcackes since I post just over a day ago....wasn't really expecting that!  Just posted it there for my Pen test team

---

### Post by Crusty Old Fart on 2010-12-12
Okay, Eric...Crash should be fixed now and output cleaned up...Try this:
```

#!/bin/bash
set -e

echo -n "Please enter the full path to your SSLStrip Log file: "
read -e LOGPATH

echo -n "Please enter the full path to your definitions file: "
read -e DEFS

NUMLINES=$(cat "$DEFS" | wc -l)

i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' "$DEFS")
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' "$DEFS")
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' "$DEFS")
  if [ $(cat "$LOGPATH" | grep $VAL1 | grep $VAL2 | grep -c $VAL3) -ge 1 ]; then
    echo $VAL1 $VAL2 $VAL3 >> /$PWD/accts.txt
  fi
  i=$[$i+1]
done

exit 0


```Also, for security and privacy reasons, I do not allow my systems to access the google domain, nor do I allow anything google to access my systems. So, please upload your program here.

---

### Post by J0hnnyBr@v0 on 2010-12-12
> **Crusty Old Fart said:**
> Okay, Eric...Crash should be fixed now and output cleaned up...Try this:
```

#!/bin/bash
set -e

echo -n "Please enter the full path to your SSLStrip Log file: "
read -e LOGPATH

echo -n "Please enter the full path to your definitions file: "
read -e DEFS

NUMLINES=$(cat "$DEFS" | wc -l)

i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' "$DEFS")
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' "$DEFS")
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' "$DEFS")
  if [ $(cat "$LOGPATH" | grep $VAL1 | grep $VAL2 | grep -c $VAL3) -ge 1 ]; then
    echo $VAL1 $VAL2 $VAL3 >> /$PWD/accts.txt
  fi
  i=$[$i+1]
done

exit 0


```Also, for security and privacy reasons, I do not allow my systems to access the google domain, nor do I allow anything google to access my systems. So, please upload your program here.

I will give this a go!

With regards to Google...yeah I understand that's why I run google sharing, its a plugin from Moxie Marlinspike he spoke about at Defcon this year.

I have only used Google for this project...but thinking sourceforge may be better....

I will get the code up as soon as I can...

Thanks,
Eric

---

### Post by J0hnnyBr@v0 on 2010-12-12
I went through it and it just echo back the values from DEF, and not the values it found in the sslstrip.log file.

I'm still poking at it on my end as well....


Best Regards,
Eric

---

### Post by Crusty Old Fart on 2010-12-12
Okay...I need a better explanation of what you wanted when you wrote:
> 
Next step would be to take the output value of the variables only.

...and...
> 
 The output still have a ton of "junk" around it.  I can work with it  the way it is, but do you think it could be cleaned up with some ease?

The way the script is running right now, when it finds a line in the log file that contains all three values of the variables, it echos the values of the variables to the accts.txt file.

If you wanted something different, please explain.

Thanks.

---

### Post by J0hnnyBr@v0 on 2010-12-12
Yes...my fault for not explaining better.

The way I explained it....the code you wrote works perfectly :)

So it does the grep, cat the line to a file so you have a bunch of junk and your values email=blah&passwd=blah, then more junk as you can see from the files I provided.

Ex:
ltmpl=default&ltmplcache=2&continue=http%3A%2F%2Fmail.google.com%2Fmail%2F%3Fui%3D2&service=mail&rm=false&dsh=3262707718393097774&ltmpl=default&ltmpl=default&scc=1&timeStmp=&secTok=&GALX=FooKNM0SYlA&Email=joeschmoe%40gmail.com&Passwd=nagnist1&signIn=Sign+in&asts=

First is to grep the entire files to find the lines with accounts, next would be to grab just tha variable values and provide instead of the entire grep'd line.

So for gmail, after the program finished it would write only this to the accounts file:

Email=value&Passwd=value

Everything else would be pruned away.


However...right now...I would just be happy with the cat/grep function outputing to the accounts.txt file.

Best regards,
Eric

---

### Post by Crusty Old Fart on 2010-12-12
> **J0hnnyBr@v0 said:**
> Yes...my fault for not explaining better.

The way I explained it....the code you wrote works perfectly :)

So it does the grep, cat the line to a file so you have a bunch of junk and your values email=blah&passwd=blah, then more junk as you can see from the files I provided.

Ex:
ltmpl=default&ltmplcache=2&continue=http%3A%2F%2Fmail.google.com%2Fmail%2F%3Fui%3D2&service=mail&rm=false&dsh=3262707718393097774&ltmpl=default&ltmpl=default&scc=1&timeStmp=&secTok=&GALX=FooKNM0SYlA&Email=joeschmoe%40gmail.com&Passwd=nagnist1&signIn=Sign+in&asts=

First is to grep the entire files to find the lines with accounts, next would be to grab just tha variable values and provide instead of the entire grep'd line.

So for gmail, after the program finished it would write only this to the accounts file:

Email=value&Passwd=value

Everything else would be pruned away.

Ah yup...I get it now. That's not a nut that I'm going to be able to crack without putting my brain into overdrive for a few hours. In the meantime,...
> 
However...right now...I would just be happy with the cat/grep function outputing to the accounts.txt file.
Here you go:
```

#!/bin/bash
set -e

echo -n "Please enter the full path to your SSLStrip Log file: "
read -e LOGPATH

echo -n "Please enter the full path to your definitions file: "
read -e DEFS

NUMLINES=$(cat "$DEFS" | wc -l)

i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' "$DEFS")
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' "$DEFS")
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' "$DEFS")
  if [ $(cat "$LOGPATH" | grep $VAL1 | grep $VAL2 | grep -c $VAL3) -ge 1 ]; then
    cat "$LOGPATH" | grep $VAL1 | grep $VAL2 | grep $VAL3 >> /$PWD/accts.txt
  fi
  i=$[$i+1]
done

exit 0

```

---

### Post by J0hnnyBr@v0 on 2010-12-12
I got it!

#!/bin/bash
set -e
#
echo -n "Please enter the full path to your SSLStrip Log file: "
read -e LOGPATH
#
echo -n "Please enter the full path to your definitions file: "
read -e DEFS
#
NUMLINES=$(cat "$DEFS" | wc -l)
i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' "$DEFS")
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' "$DEFS")
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' "$DEFS")
  for ACCTVAL in $(cat "$LOGPATH" | grep $VAL1 | grep $VAL2 | grep $VAL3); do
  echo $ACCTVAL>>/$PWD/accounts.txt
  done
  i=$[$i+1]
done
exit 0

So next is to parse through that output for just the values to get just the credentials out.

Best Regards,
Eric

---

### Post by J0hnnyBr@v0 on 2010-12-12
Agreed that the next part is more difficult...

Basically, I have the starting value....$VAL2, and then I would want to stop at the second '&' after $VAL2

Becuase we have $VAL2 (Email) an '=', the variable value an '&' $VAL3(Passwd) an '=', and the variable value and another '&'

So we want to awk or sed, or something the contents starting at $VAL2 and ending at the second '&'

Then we could always replace the & with a space to clean it up.

Gonna take a bit to chip away at that I think...

Best Regards,
Eric

---

### Post by Crusty Old Fart on 2010-12-12
Getting closer now...
```

#!/bin/bash

# ************************************************************************
# DEFINE FUNCTIONS
# ************************************************************************
function parse_log()
{
NUMLINES=$(cat "$1" | wc -l)

i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' "$1")
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' "$1")
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' "$1")
  GREPSTR="$(grep $VAL1 "$2" | grep $VAL2 | grep $VAL3)"
  if [ "$GREPSTR" ]; then

  # COMMENT OUT THE FOLLOWING LINE TO SUPPRESS OUTPUT OF $VAL1
    echo -e "\n$VAL1" >> /$PWD/accts.txt

    echo "$GREPSTR" | \
    sed '{
          s/.*'$VAL2'=/'$VAL2'=/
          s/&/ /
          s/&.*//
         }' \
    >> /$PWD/accts.txt
  fi
  i=$[$i+1]
done
}

# ************************************************************************
# RUN MAIN PROGRAM
# ************************************************************************

echo -n "Please enter the full path to your SSLStrip Log file: "
read -e LOGPATH

echo -n "Please enter the full path to your definitions file: "
read -e DEFS

parse_log "$DEFS" "$LOGPATH"

exit 0


```I included the output of $VAL1 with an echo line in the parse_log function to help with debugging. Redundancy between google.com and gmail.com was driving me nuts until I did that and saw what was happening. You can either delete it or comment it out if you want the accts.txt file to contain only credentials.

The script runs much faster now and the accts.txt file is very easy to read.

Are we having fun yet...or what?

---

### Post by J0hnnyBr@v0 on 2010-12-15
Thanks again for all  your help.

Here's where we're at...

[http://sourceforge.net/projects/easy-creds/](http://sourceforge.net/projects/easy-creds/)

Put on sourceforge so you can actually download :-p

Version 2.2 is pretty much done.  v3 is in the works, redoing menus & cleaning up function calls.


Best Regards

---

### Post by Crusty Old Fart on 2010-12-15
Since you're working on version 3, I have some improvements:
```

#Coded by Crusty Old Fart with a few updates by me - Ubuntu Forums

echo -n "Please enter the full path to your SSLStrip Log file: "
read -e LOGPATH

echo -n "Please enter the full path to your definitions file: "
read -e DEFS

NUMLINES=$(cat "$DEFS" | wc -l)

i=1
while [ $i -le $NUMLINES ]; do
  VAL1=$(awk -v k=$i 'FNR == k {print $1}' "$DEFS")
  VAL2=$(awk -v k=$i 'FNR == k {print $2}' "$DEFS")
  VAL3=$(awk -v k=$i 'FNR == k {print $3}' "$DEFS")
  VAL4=$(awk -v k=$i 'FNR == k {print $4}' "$DEFS")

  GREPSTR="$(grep -a $VAL2 "$LOGPATH" | grep -a $VAL3 | grep -a $VAL4)"
  if [ "$GREPSTR" ]; then
    echo -n "$VAL1" "- " >> /$PWD/strip-accts.txt
    echo "$GREPSTR" | \
    sed -e 's/.*'$VAL3'=/'$VAL3'=/' -e 's/&/ /' -e 's/&.*//' >> /$PWD/strip-accts.txt
  fi
  i=$[$i+1]
done

```This should run much faster because we won't have the processing overhead of doing this:
```

cat "$LOGPATH" | grep -a $VAL2 | grep -a $VAL3 | grep -a $VAL4

```twice -- once for the previous if statement (which is no longer needed since we won't use "set -e" anymore) and a second time to write to strip-accts.txt.

Also, we don't need to cat "$LOGPATH" when the grep pipeline uses it as a file parameter for the first grep as in:
```

GREPSTR="$(grep -a $VAL2 "$LOGPATH" | grep -a $VAL3 | grep -a $VAL4)"

```How's that?...Clear as mud?

---

### Post by J0hnnyBr@v0 on 2010-12-15
Excellent, included in v2.2 before posting to sourceforge

Best Regards!!

---

### Post by Crusty Old Fart on 2010-12-15
> **J0hnnyBr@v0 said:**
> Excellent, included in v2.2 before posting to sourceforge

Best Regards!!

Well, Eric:

I think we did it. I've enjoyed working with you on this little project. I don't have anything else to add to it. So, I reckon we're done and you can go ahead and mark this thread as [SOLVED] unless there's anything else you'd like to do with it.

Best wishes,

Crusty

---

### Post by J0hnnyBr@v0 on 2010-12-15
You have been a life saver!  Your code will be used by millions of pen testers worldwide ;)

I may be back bothering you again some time in the near future.

If you want to look through my code and let me know where some changes can be made, I'd be glad to incorporate.

Best Regards!

P.s.  How do I move to "SOLVED"

---

### Post by Crusty Old Fart on 2010-12-15
> **J0hnnyBr@v0 said:**
> You have been a life saver!  Your code will be used by millions of pen testers worldwide ;)


Yah...I know...that's why I get paid the BIG BUCK$  :cool: -- (an old joke among me and my friends whenever I write a script for them, all of which have been free for the asking.)

By the way, what are pen testers? In the R&D labs where I've worked in the past, pen testers were testing ink-jet print heads (pens). But, I don't see how your script relates to that kind of "pen testing".

> **J0hnnyBr@v0 said:**
> 

I may be back bothering you again some time in the near future.

If you want to look through my code and let me know where some changes can be made, I'd be glad to incorporate.



There's a fair amount of code there. I've looked at it. But, haven't studied it. You seem to be happy with the way it's working, so that's all that really matters. There are so many different ways to accomplish the same result when writing scripts that I would probably approach the whole problem completely differently and end up with a script that doesn't resemble much of what you have written. However, I suspect that most of the differences would be nothing more than my coding *style* being different than yours.

On the other hand, if you have any *problems* with it that leave you in a lurch, I'd be happy to take a look at them. For that, I'll stay subscribed to this thread for a while longer.

> **J0hnnyBr@v0 said:**
> 

P.s.  How do I move to "SOLVED"

Follow the instructions in the following post:
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

Again, Eric, it's been a pleasure. I hope you have a very Merry Christmas and a happy, healthy, and prosperous new year.

All the best to you,

Crusty

---

### Post by J0hnnyBr@v0 on 2010-12-15
A Penetration Tester is just the "industry way" of say hacker.

I am a hacker who is hired by companies to test their security posture (internal & external) and make recommendations as to how to secure it further (Usually because I have completly destroyed them)

Its a fun job.  I created a simple script for my boss who was on a pentest in Germany and didn't know Linux or how to fully use Ettercap.  It has grown into what you see today.

I honestly think it can't get much more functional.  Of course it can be tweaked, etc but I don't want to add every option under the sun.

I think v3 will be where its at...then just minor code tweaks to streamline after that.

Thanks again...I'll be looking for you again I am sure!

Best Regards,
Eric

---

### Post by thaijames on 2010-12-21
Here is a script I have been using for SSL Strip, it has the advantage that it has white and black lists so you can tell it too look for new password field  there is three parts:

#!/usr/bin/env python

#####################
# ParseLog.py
#
# By [email]z3ros3c@gmail.com[/email]
#####################

""" This file parses the sslstrip.log created by
    sslstrip for usernames and passwords (and other
    interesting information) defined in the file
    resources/definitions.sslstrip. It will also
    give you a complete list of all unknown information,
    with the exception of anything listed in the file
    resources/blacklist.sslstrip.
"""

from urllib import unquote

getIP = lambda origin: origin[origin.find('(')+1:origin.find(')')]

blacklist = []
accounts = []
definitions = {}

def getDefs(defs):
  d = {}
  for definition in defs:
    tmp = definition.split('|')
    a = tmp.pop(0)
    b = tmp.pop()
    if('\n' in b):
      b = b[:-1]
    tmp.append(b)
    d[a] = tmp[:]
  return d

def getAllVars(line):
  while('&&' in line):
    line = line.replace('&&','&')
  vars = {}
  tmp = line.split('&')
  for var in tmp:
    try:
      (a,b) = var.split('=')
      if('$' in unquote(a)):
        a = unquote(a).split('$').pop()
      if('\n' in unquote(b)):
        b = unquote(b)[:-1]
      vars[unquote(a)] = unquote(b)
    except:
      pass
  return vars

def process(origin,line):
  origin = getIP(origin)
  if(origin not in blacklist):
    vars = getAllVars(line)
    if(origin in definitions):
      definition = definitions[origin][:]
      name = definition.pop(0)
      account = "(%s) " % name
      for variable in definition:
        try:
          v = vars[variable]
        except:
          v = 'UNDEFINED'
        account += "%s = %s :: " % (variable,v)
      if('UNDEFINED' not in account):
        if(account not in accounts):
          accounts.append(account)
          account += "**NEW**"
        print(account)
    else:
      print("Unknown:\t%s" % origin)
      for var in vars:
        if(vars[var] != ""):
          print("\t%s:\t%s" % (var,vars[var]))
try:
  lines = open('sslstrip.log','r').readlines()
except:
  lines = []
try:
  blacklist = open('resources/blacklist.sslstrip','r').read().split('\n')
except:
  print("--blacklist not defined--")
try:
  accounts = open('accounts.txt','r').read().split('\n')
except:
  pass
try:
  definitions = getDefs(open('resources/definitions.sslstrip','r').readlines())
except:
  pass

try:
  line = lines.pop(0)
  while(1):
    while('POST' not in line):
      try:
        line = lines.pop(0)
      except:
        break
    process(line,lines.pop(0))
    try:
      line = lines.pop(0)
    except:
      break
except:
  print("Empty logfile.")

output = open('accounts.txt','w')
accounts.sort()
for account in accounts:
  if(account != ''):
    output.write(account + '\n')

---

### Post by thaijames on 2010-12-21
Here is the definitions file that tells it to look for passwords in a certain format:

Save it as definitions.sslstrip:

Here is an example:

accounts.craigslist.org|CraigsList|inputEmailHandle|inputPassword
digg.com|Digg|username|password
en.wikipedia.org|Wikipedia|wpName|wpPassword
en.wordpress.com|WordPress|log|pwd
exp.scg.co.th|SCG|ctlUserName|ctlPassword
hi5.com|Hi5|email|password
imgur.com|Imgur|username|password
login.aeriagames.com|AeriaGames|edit[name]|edit[pass]
login.capitalone.com|Capital One|user|password
login.facebook.com|Facebook|email|pass
login.live.com|Microsoft Live|login|passwd
login.photobucket.com|PhotoBucket|loginForm[usernameemail]|loginForm[password]
login.skype.com|Skype|username|password
login.yahoo.com|Yahoo!|login|passwd
my.screenname.aol.com|AIM|loginId|password
my.t-mobile.com|T-Mobile|txtMSISDN|txtPassword
mysprint.sprint.com|Sprint|USER|PASSWORD
secure.imdb.com|IMDB|login|password
secure.imvu.com|IMVU|avatarname|password
secure.meetup.com|MeetUp|email|password
secure.myspace.com|Myspace|Email_Textbox|Password_Textbox
signin.ebay.com|Ebay|userid|pass
slashdot.org|Slashdot|unickname|upasswd
twitter.com|Twitter|session[username_or_email]|session[password]
us.battle.net|BattleNet|accountName|password
[www.agoda.co.th|Agoda|UserName:|pwd](www.agoda.co.th|Agoda|UserName:|pwd)
[www.amazon.com|Amazon|email|password](www.amazon.com|Amazon|email|password)
[www.blogger.com|Blogger|Email|Passwd](www.blogger.com|Blogger|Email|Passwd)
[www.charter.com|Charter.com|txtMyAcctV3UserName|txtMyAcctV3Pass|txtHorWideZipCodeV3](www.charter.com|Charter.com|txtMyAcctV3UserName|txtMyAcctV3Pass|txtHorWideZipCodeV3)
[www.demonoid.com|Demonoid|nickname|password](www.demonoid.com|Demonoid|nickname|password)
[www.deviantart.com|DeviantArt|username|password](www.deviantart.com|DeviantArt|username|password)
[www.formspring.me|FormSpring|username|password](www.formspring.me|FormSpring|username|password)
[www.friendster.com|Friendster|email|password](www.friendster.com|Friendster|email|password)
[www.google.com|Google|Email|Passwd](www.google.com|Google|Email|Passwd)
[www.hi5.com|Hi5|email|password](www.hi5.com|Hi5|email|password)
[www.*************|LinkedIn|session_key|session_password](www.*************|LinkedIn|session_key|session_password)
[www.mininova.org|MiniNova|name|password](www.mininova.org|MiniNova|name|password)
[www.netflix.com|NetFlix|email|password1](www.netflix.com|NetFlix|email|password1)
[www.paypal.com|PayPal|login_email|login_password](www.paypal.com|PayPal|login_email|login_password)
[www.progressive.com|Progressive|user1|PWDpassword1](www.progressive.com|Progressive|user1|PWDpassword1)
[www.reddit.com|Reddit|user|passwd](www.reddit.com|Reddit|user|passwd)
[www.stumbleupon.com|StumbleUpon|username|password](www.stumbleupon.com|StumbleUpon|username|password)

---

### Post by thaijames on 2010-12-21
This is an example blacklist  save it as blacklist.sslstrip


Any domains on this list will be ignored when generating the report file.

Here is an example:

api.facebook.com
api.connect.facebook.com
apps.facebook.com
agoda.com
hkg.reservation.agoda.com
bl130w.blu130.mail.live.com
farmsrv.com
live.com
*.live.com
mw.50cubes.com
safebrowsing.clients.google.com
sup.live.com
svcs.ebay.com



I take no credit for any of this, this script can be found on the internet.  Look up the original poster for further information.

But it does work good.

---

### Post by J0hnnyBr@v0 on 2010-12-21
Thanks thaijames I had found that as well....but my entire script was in Bash...so I wanted to stick with that.  In addition, that script printed so much garbage to the screen.

We set about to creat a script that does the same...and I think we accomplished it.  It similarly compares against a definition file and when done posts the site and creds.

Check out the full easy-cred script at sourceforge or google projects
[http://sourceforge.net/projects/easy-creds/](http://sourceforge.net/projects/easy-creds/)

You'll find its pretty cool.

Best Regards

---

