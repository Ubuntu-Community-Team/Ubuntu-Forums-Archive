---
title: "Where it's &quot;at&quot;"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Langstracht on 2010-09-21
I've been down this "at" road before ... but I guess I didn't learn!

I have a bunch of commands that I have been running in a crontab successfully and forever.

I would like to take these commands and, instead of a "fixed schedule", make them independent of the clock and dependent on a variable start time.

So, instead of:

at 7:15 run A
at 7:21 run B
at 8:01 run C

I would have, after an arbitrary start time,

in 3 minutes run A
in 9 minutes run B
in 49 minutes run C.

I had imagined this was as simple as create a script which had a bunch of "at now +3, 9, 49 minutes command" statements and I would be off and running.

Well, off.  But certainly not running.  

I cannot get "anything to work".  Either the command(s) execute immediately (i.e. ignoring "at") or they don't execute at all.

Can anyone give me a nudge in the right direction.

Please and thanks.

---

### Post by john newbuntu on 2010-09-22
"at" works for me.  Assuming "A" to be a file either of these will run the command (permissions permitting)
```
at -f A 7:15AM
at now +3 minute -f A
```My at version is 3.1.11 and make sure that you redirect whatever is there in "A" to a file with full pathname to view the output.

---

### Post by Langstracht on 2010-09-22
O.k. here's a specific example.

I want in ten minutes to have a web page open, so:

firefox "file.html" - works fine on the command line

but for crontab I need:

export DISPLAY=:0 && firefox "file.html" - which also works fine ...

The question is what works in the form of:

at now +10 minutes blah, blah, blah.

None of the combinations of commands I've tried do.

Again, appreciate any help ...

---

### Post by john newbuntu on 2010-09-22
Put this in a file called say, "A". (Check pathnames etc first)
```
export DISPLAY=:0.0
/usr/bin/firefox /home/<userid>/file.html
```Then type this at the command line```

at now +10 minute -f A

```

---

### Post by Langstracht on 2010-09-22
And, of course, you are absolutely right.  Thank you SO MUCH.

Guess I've got a bunch of files I need to create.  Better get at it ...

---

