---
title: "Create Application Launcher with Terminal Command?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by phikai on 2009-12-22
So After finally getting my webcam to work thanks to another thread on the forums...I now need to launcher Skype using the following the command...

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

I've tried editing the skype Launcher and pasting that in and it didn't work...so I changed it to Application in Terminal and I get an error:

"There was an error creating the child process for this terminal."

Any help/thoughts?

Thanks!

---

### Post by Barriehie on 2009-12-22
> **phikai said:**
> So After finally getting my webcam to work thanks to another thread on the forums...I now need to launcher Skype using the following the command...

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

I've tried editing the skype Launcher and pasting that in and it didn't work...so I changed it to Application in Terminal and I get an error:

"There was an error creating the child process for this terminal."

Any help/thoughts?

Thanks!

Will skype launch if you enter```
/usr/lib32/libv4lcompat.so skype
``` from the CLI?  If so then you could create an alias:
alias goskype="/usr/lib32/libv4lcompat.so skype"

Barrie

---

### Post by phikai on 2009-12-22
> **Barriehie said:**
> Will skype launch if you enter```
/usr/lib32/libv4lcompat.so skype
``` from the CLI?  If so then you could create an alias:
alias goskype="/usr/lib32/libv4l**/v4l1**compat.so skype"

Barrie

I couldn't get it to launch using that command...I corrected the path...

---

### Post by sisco311 on 2009-12-22
try:
```
bash -c "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype"
```

---

### Post by phikai on 2009-12-22
> **sisco311 said:**
> try:
```
bash -c "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype"
```

Awesome! That worked as the command for the launcher. Is there anyway to close the terminal window that opens after it launches? or does it need to stay open?

---

### Post by Tulth on 2009-12-22
I'm interested in the best answer to this as well.  What I have been doing is create a **~/my_launchers** folder, and putting launcher scripts for things like this in that folder.  In your case the script would look something like:
```
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

Then in the panel launcher i'd just put **/home/<my user>/my_launchers/<script name>**

Be sure to **chmod a+x** all your launcher scripts to make them executable.

---

### Post by phikai on 2009-12-22
> **Tulth said:**
> I'm interested in the best answer to this as well.  What I have been doing is create a **~/my_launchers** folder, and putting launcher scripts for things like this in that folder.  In your case the script would look something like:
```
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```Then in the panel launcher i'd just put **/home/<my user>/my_launchers/<script name>**

Be sure to **chmod a+x** all your launcher scripts to make them executable.

That also worked for me...seems to be about the same either way, and if anything yours might be a bit easier to reference and share with others...

I changed to it ;)

I still wish there was a way to close the terminal window though...

---

### Post by sisco311 on 2009-12-22
> **phikai said:**
> That also worked for me...seems to be about the same either way, and if anything yours might be a bit easier to reference and share with others...

I changed to it ;)

I still wish there was a way to close the terminal window though...

You don't have to run it in a terminal. Deselect the *Run in terminal* checkbox.

---

### Post by phikai on 2009-12-22
So I've done the Launcher folder with scripts going there...

My Skype script is:

```
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

Works fine aside from the terminal window... so I found that I could run the following from terminal and it opens skype and closes the window:


```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype & exit
```


But if I replace that line in my script it doesn't work...

---

### Post by asmoore82 on 2009-12-22
you could also use the `env` command - just put it ahead of everything else...
```

env LD_LIBRARY=/path/to/lib.so apptolaunch
```
this is how automagic WINE launchers handle the situation.

---

### Post by phikai on 2009-12-22
> **sisco311 said:**
> You don't have to run it in a terminal. Deselect the *Run in terminal* checkbox.

Well that solved it! THANKS!

Why don't I need to run it in Terminal? Does the bash part take care of that? sorry...uber n00b here

---

### Post by bodhi.zazen on 2009-12-22
If you run the command in a terminal, the application (skype) will exit when you close the terminal.

You need to use nohup , detach, or screen

```
nohup bash -c "LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype &"; exit
```

---

