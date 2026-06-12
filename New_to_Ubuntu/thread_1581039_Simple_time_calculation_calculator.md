---
title: "Simple time calculation calculator?"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by Kellemora on 2010-09-24
Hi Gang

Is there a program in Synaptic that lets you add hours to the current 12 hour clock time and it will give you what time it would be after that many hours elapsed?

EG:  It's currently 9:15AM Friday, in 21 hours it will be ? (Day and Time?)

It's OK if it only works in even hourly increments!

Anything would beat the MANUAL system I'm using right now, hi hi....

A piece of barn slat, divided into 100 increments for hours.
The first 24 increments are for the current time.
Then I have shorter sticks precut to 12, 16, 20, 28, 30, 40, etc. hours, all the way up to 80 hours.
By placing the precut stick of hours over the barn slat, with it's left edge on the current time, the right edge then shows me the time and day the time period will expire.

My accounting software will do this, but I don't want to use such a powerful (memory hog) package for simple time tracking.

My wife has a recipe calculator that does this in reverse.  You enter the time you want to serve dinner, the time each item needs to cook, and it tells you when to start on each item so they all come out at the same time.

Thanks

TTUL
Gary

---

### Post by philinux on 2010-09-24
I would use Open office spreadsheet for this.

---

### Post by Old_Man_Unix on 2010-09-24
Easy - use the Linux** date** function in a terminal.  Such as:

```

$ date -d "today +3 days"

$ date -d "today +11 hours"

$ date -d "today +5 days +8 hours"

```or whatever you want.  

The output will be the current time plus whatever interval you specify 

There's a lot more that you can do with **date**.  Just pull up the man page to see it all.

---

### Post by Kellemora on 2010-09-24
Thank You Old Man

That is EXACTLY what I was wanting!!!!!

Fast Simple and accurate, hi hi....

TTUL
Gary

---

### Post by Kellemora on 2010-09-24
Hi Phil

I'll give that a try also.

But terminal is about as light as it gets.  After the first entry, just hit the up arrow, change the number, hit end and enter.

I never did learn bash or how to write little programs like I used to know how to do in Basic eons ago.  I was actually quite good at it too!  Basic that is.
I really should do that!

Thanks
TTUL
Gary

---

### Post by KIAaze on 2010-09-24
I have a python script for that (although "date" is probably simpler indeed depending on your needs):
_time_op.py:_
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import datetime
import re
import sys
import getopt

CALCULATION_STRING = sys.argv[1]
if len(sys.argv)>2:
  FORMAT_STRING = sys.argv[2]

#TODO: Use "%Y/%m/%d %H:%M" eventually.

pattern=re.compile('(d?)(\d+):(\d+):(\d+) ([\+-]) (d?)(\d+):(\d+):(\d+)')
m=pattern.match(CALCULATION_STRING)
m.groups()
d1 = m.group(1)
H1 = int(m.group(2))
M1 = int(m.group(3))
S1 = int(m.group(4))
op = m.group(5)
d2 = m.group(6)
H2 = int(m.group(7))
M2 = int(m.group(8))
S2 = int(m.group(9))

#print d1
#print H1
#print M1
#print op
#print d2
#print H2
#print M2

today=datetime.datetime.today()

if d1=='d':
  t1 = datetime.timedelta(0,H1*60*60+M1*60+S1)
else:
  t1 = datetime.datetime(today.year,today.month,today.day,H1,M1,S1)

if d2=='d':
  t2 = datetime.timedelta(0,H2*60*60+M2*60+S2)
else:
  t2 = datetime.datetime(today.year,today.month,today.day,H2,M2,S2)

if op=='+':
  result=t1+t2
else:
  result=t1-t2

#if we have a timedelta object
if d1=='' and d2=='':
  result = datetime.datetime(1901,1,1)+result

#print result
#print str(result.hour)+':'+str(result.minute)
if len(sys.argv)==3:
  print result.strftime(FORMAT_STRING)
else:
  print result.strftime('%H:%M:%S')

#now=datetime.datetime.now()

#H=int(now.strftime("%H"))
#M=int(now.strftime("%M"))
#S=int(now.strftime("%S"))

#diff = datetime.datetime.today() - datetime.datetime(2010, 6, 6, 23, 6)
#print diff.days,"days ", diff.seconds/60/60,"hours ", diff.seconds/60 - (diff.seconds/60/60 * 60),"minutes "

#end=now+HMS
#rem=end-now

#def main():
    #if len(sys.argv)==1:
	    #usage()
	    #sys.exit()
    #try:
        #opts, args = getopt.getopt(sys.argv[1:], "hivs:", ["help", "increment", "version", "set="])
    #except getopt.GetoptError, err:
        ## print help information and exit:
        #print str(err) # will print something like "option -a not recognized"
        #usage()
        #sys.exit(2)
        
    #for o, a in opts:
        #if o in ("-h", "--help"):
            #usage()
            #sys.exit()
        #elif o in ("-i", "--increment"):
	    #print "Incrementing version"
	    #old_version=show_version()
	    #new_version=nextversion(old_version)
	    #change_version_all(old_version,new_version)
            #sys.exit()
        #elif o in ("-v", "--version"):
	    #print "Current version:"
	    #old_version=show_version()
            #sys.exit()
        #elif o in ("-s", "--set"):
	    #new_version=a
	    #print "Setting version to "+new_version
	    #old_version=show_version()
	    #change_version_all(old_version,new_version)
            #sys.exit()
        #else:
            #assert False, "unhandled option"

#if __name__ == "__main__":
    #main()

```

_Usage:_
```

#substract times:
time_op.py "HH:MM:SS - HH:MM:SS"
#Add or substract time deltas:
time_op.py "HH:MM:SS + dHH:MM:SS"
time_op.py "HH:MM:SS - dHH:MM:SS"
#specify an output format (similar to "date"):
time_op.py "HH:MM:SS - HH:MM:SS" +FORMAT
time_op.py "HH:MM:SS + dHH:MM:SS" +FORMAT
time_op.py "HH:MM:SS - dHH:MM:SS" +FORMAT

```

_Examples:_
```
ubuntu@ubuntu:~/Desktop$ date +%H:%M:%S
16:12:24
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 + d16:12:24"
08:24:48
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 + d2:12:24"
18:24:48
ubuntu@ubuntu:~/Desktop$ python time_op.py "d16:12:24 + 2:12:24"
18:24:48
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 + d2:12:24"
18:24:48
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - d2:12:24"
14:00:00
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - 2:12:24"
14:00:00
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - 2:12:24"
14:00:00
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - 2:12:24" +%H
+14
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - 2:00:2" +%H
+14
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - 2:00:2" +%M
+12
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - 2:00:2" +%S
+22
ubuntu@ubuntu:~/Desktop$ python time_op.py "16:12:24 - 2:00:2"
14:12:22
ubuntu@ubuntu:~/Desktop$ 

```

---

### Post by Kellemora on 2010-09-26
Hi KIA

Thanks for going to the trouble to post all of that, however, it's WAY over my head....

I spent over two hours just studying the MAN page for DATE and can't make heads or tails out of it.

What I was looking for in the MAN pages was a way to make the Time Displayed using the DATE in 12 hour format with AM or PM, just to make it a little easier to read quickly.
But it's no biggie if it don't work that way, I have fingers and toes, hi hi.....

I would have never figured out what the line that reads

  -d, --date=STRING
              display time described by STRING, not ‘now’

ever means...... makes NO SENSE to me at all!

It shows a %I and also a %l which MIGHT be what I'm looking for?
But no example of WHERE do you put this instruction, if it is an instruction.

Would it be written
date -d %l "today +20 hours"
or 
date -d "today %l +20 hours"
or
or
or??????

Nowhere in the MAN pages, does it show the word TODAY as a valid FORMAT word AND it uses the word OPTION to Describe the -d listed under GIVEN FORMAT...........
How is someone supposed to understand this?
Options should be listed as OPTIONS
Formats should be listed as FORMATS (with examples of how they are used).
Options should never be called GIVEN FORMAT.......

But, if using %l will do what I want it to do, WHERE does it get put?

Thanks

TTUL
Gary

---

### Post by KIAaze on 2010-09-26
The syntax for "FORMAT" is explained at the beginning of the man page:
```
       date [OPTION]... [+FORMAT]
```
The important thing is the "+" sign.

ex:
```
# %I     hour (01..12)
$ date +%I
11

# %r     locale's 12-hour clock time (e.g., 11:11:04 PM)
$ date +%r
11:46:41 pm BST

# a custom date+time string
$ date +%Y%m%d_%H%M%S
20100926_234658

```

You can get more extended info using (useful if you want to use the "--date=STRING" option):
```
info date
```

---

### Post by Kellemora on 2010-09-27
Thanks KIA

What I'm using now is
$ date -d "today +20 hours"
The only thing I change each time is the +20 to +40 etc.
The readout might be 19:34:16

So then, would this be proper?

$ date -d +%I "today +20 hours"
or
$ date -d +%l "today +20 hours"

One is a Capital I, the other is a lower case L.


TTUL
Gary

---

### Post by KIAaze on 2010-09-27
Just try it! :)
"date" is not a dangerous command like "rm" (for removing files). So, as long as you don't run it as root or with sudo, there's not much danger. And even as root, I don't think you can do much damage with "date" alone, but it's not recommended to play around as root.

To answer your question: Both of your examples fail because you put the FORMAT string ("+%*") between the "-d" option and its input ("today +20 hours").

Also, the difference between %I and %l is explained in the man page of "date":
```
       %I     hour (01..12)
       %l     hour ( 1..12)

```

Here are a few examples:
```
$  date -d "today +20 hours" +%I
11
$  date -d "today +10 hours" +%I
01
$  date -d "today +10 hours" +%l
 1
$  date -d "today +10 hours" +%r
01:25:00 AM
$  date +%r -d "today +10 hours"
01:25:06 AM

```
Note that you can put the format string before or after the date string, even though according to the man page it should be at the end. (maybe it doesn't commute with all options)

---

### Post by Kellemora on 2010-09-27
Thanks KIA

The info date page wasn't much help, but the date --help page was a little helpful.

But you'll note that using the +%r that the day no longer appears.
The day is important with the length of times I'm working with.

So if I have
gary@Asus64AMD5200Ubuntu:~$ date +%r -d "today +160 hours"
07:33:41 AM
or
gary@Asus64AMD5200Ubuntu:~$ date -d "today +160 hours" +%r
07:33:54 AM
but using what I had before I would get
gary@Asus64AMD5200Ubuntu:~$ date -d "today +160 hours"
Mon Oct  4 07:35:22 EDT 2010
gary@Asus64AMD5200Ubuntu:~$ date -d "today +80 hours"
Thu Sep 30 23:36:43 EDT 2010

I am playing around trying different things.
Most say (you messed up go read the man page), hi hi........

I don't need the Month or Year.
If I could get it to just say the Day and 12-hour time AM or PM of a future event based on +60 hours, where the +60 is the only variable.

EG: Mon  06:23 PM

I will play with it myself and perhaps learn something!
The first time I tried it on my own, it reset my computers internal clock.
Which is why I was leery of messing around.

Again, thanks for all your help.....
This OLDE Kraut has a thick skull, hi hi.......

TTUL
Gary

---

### Post by Kellemora on 2010-09-27
Hi KIA

Thanks to your help, I finally figured it out!

Here is what I came up with!

gary@Asus64AMD5200Ubuntu:~$ date +%A_%I:%M_%p -d "today +60 hours"
Thursday_03:57_AM

I couldn't figure out how to make a space, but found an underscore works.

I still have not figured out WHERE the "STRING" information is learned from?

I'm marking this solved, now that I have what I need and showing what I need.

Again, thanks for your help!

TTUL
Gary

---

### Post by KIAaze on 2010-09-27
> **Kellemora said:**
> 
Most say (you messed up go read the man page), hi hi........

Where? :confused:

> **Kellemora said:**
> 
The first time I tried it on my own, it reset my computers internal clock.
Which is why I was leery of messing around.

Oops. Mea culpa. Yes, it seems you can set the local date and time with it. Didn't know that. ^^'

> **Kellemora said:**
> 
gary@Asus64AMD5200Ubuntu:~$ date +%A_%I:%M_%p -d "today +60 hours"
Thursday_03:57_AM

Ah, yes, I forgot to give an example combining format specifiers.

> **Kellemora said:**
> 
I couldn't figure out how to make a space, but found an underscore works.

Just add quotes (or the escape character "\"):
```
$  date +"%H %M"
01 46
$  date "+%H %M"
01 46
$  date '+%H %M'
01 46
$  date +'%H %M'
01 46
$  date +"%A %I:%M %p" -d "today +60 hours"
Thursday 01:47 PM
$  date +%A\ %I:%M\ %p -d "today +60 hours"
Thursday 01:48 PM

```

> **Kellemora said:**
> 
I still have not figured out WHERE the "STRING" information is learned from?

cf end of "man date":
```
info coreutils 'date invocation'
```
or
```
info coreutils date
```
Or online for convenience:
[http://www.fifi.org/cgi-bin/info2www?(sh-utils)Date+input+formats](http://www.fifi.org/cgi-bin/info2www?(sh-utils)Date+input+formats)

Press "h" for help in using the info page.

---

### Post by Kellemora on 2010-09-28
Hi KIA

Thanks for the info and that LINK, now I finally know where they came up with using the word "today".

Lot's of good info to learn there!

Thanks!

TTUL
Gary

---

