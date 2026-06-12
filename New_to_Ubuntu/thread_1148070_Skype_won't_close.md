---
title: "Skype won't close"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by Auslegung on 2009-05-04
I have Skype 2.0 for Linux on 9.04 UNR and when I try to close Skype it freezes.  If I click on force quit the Skype window goes away, but when running top it's still there and using about 95% of my cpu.  If I do killall skype -v it says it was successful, but again when running top it's still there and using 95%.  

Any ideas?

---

### Post by nhasian on 2009-05-04
try kill -9 instead of killall.

---

### Post by Auslegung on 2009-05-04
> **nhasian said:**
> try kill -9 instead of killall.

I did that and this is what I got:

```
$ kill -9
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]

```

I looked at the man page for kill and tried to see if something else would work but it's not well-written (at least to me).

---

### Post by nhasian on 2009-05-05
sorry i should have been more specific.  you have to include the PID (process ID) at the end of the statement.  for example if the processID is 1234 then you would type:

```
sudo kill -9 1234
```

to see what the PID is for a running program, simply type:

```
top
```

press 'q' to exit out of top.

---

### Post by llamabr on 2009-05-06
Or, more specifically:

```
ps aux | grep skype
```

Then use kill -9 on the pid

---

### Post by Holmen on 2009-05-28
Or; Run top, press 'k', type the PID of Skype, press enter and then enter 9 as signal.

---

### Post by fatality_uk on 2009-05-28
> **Holmen said:**
> Or; Run top, press 'k', type the PID of Skype, press enter and then enter 9 as signal.

Nice. I like this solution :)
Thanks

---

### Post by Paqman on 2009-05-28
I like xkill. Just Alt-F2, type xkill and click on the misbehaving app. No faffing around with process IDs.

---

### Post by Eudaimon on 2011-10-10
Thanks Holmen, worked for me!

---

### Post by no2498 on 2011-10-10
look in your auto startup programs and un click skype
windows has its hand in skype now days

---

### Post by mikejonesey on 2011-10-10
> **Auslegung said:**
> I have Skype 2.0 for Linux on 9.04 UNR and when I try to close Skype it freezes.  If I click on force quit the Skype window goes away, but when running top it's still there and using about 95% of my cpu.  If I do killall skype -v it says it was successful, but again when running top it's still there and using 95%.  

Any ideas?


for futur ref to those looking to kill all instances of an app... alike kill, killall also accepts signals... by default sigterm, however this relies on the app... to get a list of signnals availible kill -l and to kill all instances of an app by name with a forceful end... 

```
killall -s SIGKILL skype
```or
```
killall -s -9 skype
```or one by one...
```
ps -eo pid,comm | grep -v grep | grep -i skype | cut -d " " -f 1 | xargs kill -9
```that example bears in mind i've customised my cut with an alias to simplify space delimitation but you get the idea...

---

### Post by mikejonesey on 2011-10-10
or awk takes care easyer... with it's print ie... echo "abc  def hij" | awk '{print $2}'... user prefs...

---

### Post by no2498 on 2011-10-10
look in your auto startup programs and un click skype from auto start
 windows has its hand in skype now days

---

### Post by mikejonesey on 2011-10-10
i swear the download link for linux skype used to be more prodominant? now we just have a little link at the bottom of the page... (as with osx) hmm...

---

