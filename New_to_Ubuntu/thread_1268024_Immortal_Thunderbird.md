---
title: "Immortal Thunderbird"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by viodelin on 2009-09-16
I am trying to point Thunderbird to the drive where I keep my profile. However, Thunderbird seems to be running in the background although I did not open it after installation. How can I kill it with a command line?
Alt-F2 doesnt work because I have no window to point Xkill at.
I'd be grateful for some help.
M:confused:

---

### Post by LewRockwell on 2009-09-16
wasn't that the "Fabulous Thunderbirds"

[http://en.wikipedia.org/wiki/The_Fabulous_Thunderbirds](http://en.wikipedia.org/wiki/The_Fabulous_Thunderbirds)

[http://en.wikipedia.org/wiki/Jimmie_Vaughan](http://en.wikipedia.org/wiki/Jimmie_Vaughan)

[http://www.jimmievaughan.com/](http://www.jimmievaughan.com/)




guess this link should be here as well:

[http://en.wikipedia.org/wiki/Mozilla_Thunderbird](http://en.wikipedia.org/wiki/Mozilla_Thunderbird)

.

---

### Post by katakaio on 2009-09-16
[This link]("http://ubuntuforums.org/showthread.php?t=225274") describes how to kill processes from the command line. In your case, you'd want to kill *thunderbird* and *thunderbird-bin* processes, most likely.

---

### Post by indytim on 2009-09-16
To kill a process, try (in command line mode):

```

$ ps aux

```

After you have identified the process that you want to kill

```

$ kill -9 <insert process id number>

```

-IndyTim

---

### Post by wojox on 2009-09-16
Open a terminal, run 

```
top
```

Press k

Enter pid of process.

---

### Post by viodelin on 2009-09-16
Thanks for your replies.
killall thunderbird resulted in "thunderbird: no process killed"

ps -e and ps -aux are interesting because they show the hundreds of processes running in the background (among them things like bluetooth!?). None of these processes bear the words "thunderbird" or even "mozilla". How can I guess?

(How about these?
[http://www.bbc.co.uk/cult/anderson/thunderbirds/](http://www.bbc.co.uk/cult/anderson/thunderbirds/)
)

---

### Post by oldfred on 2009-09-16
It may not be running but the parentlock file was not deleted.
Info here:
[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by LewRockwell on 2009-09-16
> **viodelin said:**
> Thanks for your replies.
killall thunderbird resulted in "thunderbird: no process killed"

ps -e and ps -aux are interesting because they show the hundreds of processes running in the background (among them things like bluetooth!?). None of these processes bear the words "thunderbird" or even "mozilla". How can I guess?

(How about these?[http://www.bbc.co.uk/cult/anderson/thunderbirds/](http://www.bbc.co.uk/cult/anderson/thunderbirds/))

kewl!

try ps -ax

.

---

### Post by wojox on 2009-09-16
No need to guess, if it were running it would say thunderbird

---

### Post by viodelin on 2009-09-16
Thanks all, the link pointed me in the right direction. It couldn't find the profile because I changed the path in the .ini file to point to a different partition and the syntax in the path was wrong.

HOWEVER, now thunderbird is empty - i.e. it doesn't come up with my profile, which makes me think that I ought to get into that -profilemanager thingy which doesn't work for me either. 

maria@labonita:~$ ./mozilla-thunderbird/ -profilemanager
bash: ./mozilla-thunderbird/: No such file or directory

What am I doing wrong?

Thank you,

---

### Post by cariboo on 2009-09-16
I always use:

```
ps ax | grep <application>
```

If i'm looking for a specific program eg:

```
ps ax | grep thunderbird
```

You will get a result back if thunderbird is running. If it isn't running, it just echo back the grep thunderbird command.

---

### Post by tad1073 on 2009-09-16
open a terminal and type:
```
thunderbird -P
```

---

### Post by viodelin on 2009-09-16
IT WORKED!!!
Thank you SO much Tad!
:guitar:

---

### Post by tad1073 on 2009-09-16
> **viodelin said:**
> IT WORKED!!!
Thank you SO much Tad!
:guitar:

your welcome

---

### Post by tad1073 on 2009-09-16
you can do that with firefox also, just replace thunderbird with firefox.

I use both to set my profile folders on a seperate ntfs partition so they will be synced between OS's

---

### Post by viodelin on 2009-09-16
Yes, that was the idea. Now I can use Ubuntu on a day to day basis.

---

