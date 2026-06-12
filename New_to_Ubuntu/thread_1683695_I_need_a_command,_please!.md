---
title: "I need a command, please!"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by constellanation on 2011-02-07
I'm trying to capture some video of the terminal for a small video project, and I need some nonharmful commands that will run with many lines in the terminal for a decent amount of time.

Got any ideas, I'd like it to mimic what start up would look like if possible.

Thanks in advance.

---

### Post by rvchari on 2011-02-07
the easiest way is to issue sudo apt-get update command.
if u have enough repositories, the time taken will be fairly good to complete ur tiny video project.
i got this idea instantly coz i could visualise u need something to run in terminal when the shot is taken, if i m not mistaken !!!

---

### Post by Girya on 2011-02-07
> **constellanation said:**
> I'm trying to capture some video of the terminal for a small video project, and I need some nonharmful commands that will run with many lines in the terminal for a decent amount of time.

Got any ideas, I'd like it to mimic what start up would look like if possible.

Thanks in advance.

this might be to much but if you installed virtualbox then you could screen capture an actual boot.

---

### Post by rvchari on 2011-02-07
if u need to show start up, the more common way would be in install ubuntu on a VM and boot it with full screen mode so total boot up sequence is captured on ur video.

---

### Post by constellanation on 2011-02-07
> **rvchari said:**
> the easiest way is to issue sudo apt-get update command.
if u have enough repositories, the time taken will be fairly good to complete ur tiny video project.
i got this idea instantly coz i could visualise u need something to run in terminal when the shot is taken, if i m not mistaken !!!

That one could work, but you're right I need to actually see more the computer "working" then actual results.  though not the intention think cheesy sci fi movies =)


> **Girya said:**
> this might be to much but if you installed virtualbox then you could screen capture an actual boot.

Yeah that is a bit more than I would like to do for this, though if I get decent enough results this time, I might consider it for "authenticity"

---

### Post by tekkidd on 2011-02-07
Try 
```
sudo apt-get update
```

---

### Post by constellanation on 2011-02-07
Tried sudo apt-get update. It is too quick :)
 it's only a couple of seconds of checking...

---

### Post by constellanation on 2011-02-07
I actually have another idea, same vain. I could do a series of commands to stretch it out.

what are some good ones? like check system settings, computer hardware, etc?

---

### Post by slooksterpsv on 2011-02-07
you could do like:

```

lshw && lsmod && df && for f in /etc/*/*; do if [ -f $f ]; then  cat $f; fi; done

```

Which does a lot, but nothing harmful.

EDIT:
lshw - gives information about your hardware
lsmod - gives information about loaded modules
df - shows partition information
for f in /etc/*/*; do if [ -f $f ]; then cat $f; fi; done - outputs all the config files in the /etc/ directory and 1 level sub directory, although this will give you weird text as some of it's not text, but actual binary code.

---

### Post by uRock on 2011-02-07
```
ping
```

---

### Post by constellanation on 2011-02-07
> **slooksterpsv said:**
> you could do like:

```

lshw && lsmod && df && for f in /etc/*/*; do if [ -f $f ]; then  cat $f; fi; done

```

Which does a lot, but nothing harmful.

EDIT:
lshw - gives information about your hardware
lsmod - gives information about loaded modules
df - shows partition information
for f in /etc/*/*; do if [ -f $f ]; then cat $f; fi; done - outputs all the config files in the /etc/ directory and 1 level sub directory, although this will give you weird text as some of it's not text, but actual binary code.

So this is how neo got into the matrix? It's oddly fascinating, wow.  I feel like i just witnessed my compute on drugs

that definitely gives me enough "footage" thank you.

---

### Post by constellanation on 2011-02-07
> **uRock said:**
> ```
ping
```

that is rather short, when I try to add the options that come up, it says they need arguments?

---

### Post by quadproc on 2011-02-07
> **constellanation said:**
> that is rather short, when I try to add the options that come up, it says they need arguments?
Yes, ping needs an address to ping.  Try
```
ping 127.0.0.1
```

quadproc

---

### Post by constellanation on 2011-02-07
Ahh that's how that works. 

Thank you all, I think I'm going to go with a combination of a few codes, and the jibberish as well.

Thanks again!

---

### Post by tjwoosta on 2011-02-08
I think this is what your looking for ;)

[http://ubuntuforums.org/showthread.php?t=470386](http://ubuntuforums.org/showthread.php?t=470386)

Its a script that when run will display all kinds of fake crap to make it look like your a hacker :)

simply unzip, cd into the directory thats extracted, and run

```
./script_main.sh 100
``` (where 100 is the number of actions)

EDIT:
oh yea, to cancel the script just hit ctrl-c while the terminal window is selected.

---

### Post by dostumai on 2011-02-08
You could try:
```
top
```
That gets people staring blankly in wonder, or you could try [this thread](http://ubuntuforums.org/showthread.php?t=470386) and impressing people with utter nonsense.

---

### Post by rvchari on 2011-02-08
> **constellanation said:**
> Tried sudo apt-get update. It is too quick :)
 it's only a couple of seconds of checking...


add some repositories and then issue this command, u can dely the timing by checking all check boxes in the other repositories tab of synaptic. once u do this, u can see how long it takes in terminal to update. more the repositories, more the time....

u can always uncheck and reload after ur purpose is solved to speed up

---

### Post by uRock on 2011-02-08
> **rvchari said:**
> add some repositories and then issue this command, u can dely the timing by checking all check boxes in the other repositories tab of synaptic. once u do this, u can see how long it takes in terminal to update. more the repositories, more the time....

u can always uncheck and reload after ur purpose is solved to speed up
That can be dangerous if someone checks the box for pre-released software.

---

### Post by liquidxit2 on 2011-02-08
> **uRock said:**
> ```
ping
```

This right here. will print out on the screen until you kill the process with ctrl - c.

---

### Post by uRock on 2011-02-08
Play Star Wars in the terminal. ```
telnet towel.blinkenlights.nl
```

---

### Post by rvchari on 2011-02-08
> **uRock said:**
> That can be dangerous if someone checks the box for pre-released software.

then we can simply remove those repositories and reload synaptic...
hope my perception is correct in safeguarding what you said.

---

### Post by uRock on 2011-02-08
> **rvchari said:**
> then we can simply remove those repositories and reload synaptic...
hope my perception is correct in safeguarding what you said.
If one ran apt-get update && apt-get upgrade after adding the repo, then the packages will be installed, then when the repos are removed, the newly added packages will not be removed.

---

### Post by renkinjutsu on 2011-02-09
nothing says moviehacker like scrolling lines from a kernel compile.

---

### Post by slooksterpsv on 2011-02-09
> **renkinjutsu said:**
> nothing says moviehacker like scrolling lines from a kernel compile.

I whole heartedly agree! I love watching a compile, it's amazing.

---

### Post by rvchari on 2011-02-09
> **uRock said:**
> If one ran apt-get update && apt-get upgrade after adding the repo, then the packages will be installed, then when the repos are removed, the newly added packages will not be removed.

its not necessary to issue sudo apt-get upgrade command. update will add the repos, when the repo is updated, there is some more time available for taking the video capture as desired... thats what i had meant !!
once the purpose is solved, repos can be removed and updated again to get back to original.

---

### Post by uRock on 2011-02-09
> **rvchari said:**
> its not necessary to issue sudo apt-get upgrade command. update will add the repos, when the repo is updated, there is some more time available for taking the video capture as desired... thats what i had meant !!
once the purpose is solved, repos can be removed and updated again to get back to original.
That would be work.:p One would have to ignore Update Manager if it opened.

It is habit for me to run apt-get update && apt-get dist-upgrade as one command.

---

