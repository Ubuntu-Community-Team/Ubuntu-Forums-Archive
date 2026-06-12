---
title: "Error in Add/Remove..."
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Dr.Vista on 2009-05-16
Every time I try uninstalling or installing software in Add/Remove I get the following error message.
```
E: ufw: subprocess post-installation script returned error exit status 1
```I'm currently using Ubuntu 9.10 Jaunty Jackalope.

My log of the incident.
```
2009-05-16 22:03:10 startup packages configure
2009-05-16 22:03:10 configure ufw 0.27-0ubuntu2 0.27-0ubuntu2
2009-05-16 22:03:10 status half-configured ufw 0.27-0ubuntu2
2009-05-16 22:04:07 startup packages remove
2009-05-16 22:04:07 status installed agave 0.4.5-2
2009-05-16 22:04:07 remove agave 0.4.5-2 0.4.5-2
2009-05-16 22:04:07 status half-configured agave 0.4.5-2
2009-05-16 22:04:09 status half-installed agave 0.4.5-2
2009-05-16 22:04:09 status triggers-pending man-db 2.5.5-1build1
2009-05-16 22:04:09 status half-installed agave 0.4.5-2
2009-05-16 22:04:09 status config-files agave 0.4.5-2
2009-05-16 22:04:09 status config-files agave 0.4.5-2
2009-05-16 22:04:09 status installed bluefish 1.0.7-6ubuntu2
2009-05-16 22:04:09 remove bluefish 1.0.7-6ubuntu2 1.0.7-6ubuntu2
2009-05-16 22:04:09 status half-configured bluefish 1.0.7-6ubuntu2
2009-05-16 22:04:09 status half-installed bluefish 1.0.7-6ubuntu2
2009-05-16 22:04:09 status half-installed bluefish 1.0.7-6ubuntu2
2009-05-16 22:04:09 status triggers-pending shared-mime-info 0.60-1
2009-05-16 22:04:09 status half-installed bluefish 1.0.7-6ubuntu2
2009-05-16 22:04:09 status config-files bluefish 1.0.7-6ubuntu2
2009-05-16 22:04:09 status config-files bluefish 1.0.7-6ubuntu2
2009-05-16 22:04:09 trigproc man-db 2.5.5-1build1 2.5.5-1build1
2009-05-16 22:04:09 status half-configured man-db 2.5.5-1build1
2009-05-16 22:04:09 status installed man-db 2.5.5-1build1
2009-05-16 22:04:09 trigproc shared-mime-info 0.60-1 0.60-1
2009-05-16 22:04:09 status half-configured shared-mime-info 0.60-1
2009-05-16 22:04:10 status installed shared-mime-info 0.60-1
2009-05-16 22:04:11 startup packages configure
2009-05-16 22:04:11 configure ufw 0.27-0ubuntu2 0.27-0ubuntu2
2009-05-16 22:04:11 status half-configured ufw 0.27-0ubuntu2
2009-05-16 22:04:12 startup packages configure
2009-05-16 22:04:12 configure ufw 0.27-0ubuntu2 0.27-0ubuntu2
2009-05-16 22:04:12 status half-configured ufw 0.27-0ubuntu2

```

---

### Post by SunnyRabbiera on 2009-05-16
open a terminal and try this command:
sudo apt-get update

Make sure no other package managers are open though.
I want to see if any errors occur

---

### Post by Dr.Vista on 2009-05-16
> **SunnyRabbiera said:**
> open a terminal and try this command:
sudo apt-get update

Make sure no other package managers are open though.
I want to see if any errors occur
Thank you for the fast reply. No errors have occured yet. I have to see by installing a program.

---

### Post by SunnyRabbiera on 2009-05-16
Will do, there might be an issue with add/remove but if so we have other methods to install software on Ubuntu.

---

### Post by Dr.Vista on 2009-05-16
> **SunnyRabbiera said:**
> Will do, there might be an issue with add/remove but if so we have other methods to install software on Ubuntu.
Same errors.

---

### Post by Joeb454 on 2009-05-16
If there is still an issue, try running ```
sudo aptitude install -f
``` And see if that resolves it :)

---

### Post by SunnyRabbiera on 2009-05-16
Did you try synaptic?
There might be an issue with the server you are using, or something wrong with apt itself.
This might need some detective work but lets eliminate some possibilities.

---

### Post by Dr.Vista on 2009-05-16
> **Joeb454 said:**
> If there is still an issue, try running ```
sudo aptitude install -f
``` And see if that resolves it :)
I tried that too and that doesn't work either.

---

### Post by SunnyRabbiera on 2009-05-16
Did you try a system restart?
Sometimes the package manager hangs in the background and the only way to patch is to restart.

---

### Post by Dr.Vista on 2009-05-16
> **SunnyRabbiera said:**
> Did you try a system restart?
Sometimes the package manager hangs in the background and the only way to patch is to restart.
I'll try that. Be right back in a minute.

---

### Post by SunnyRabbiera on 2009-05-16
> **Dr.Vista said:**
> I'll try that. Be right back in a minute.

Not saying it will resolve your issue but its worth a shot.

---

### Post by Dr.Vista on 2009-05-16
> **SunnyRabbiera said:**
> Not saying it will resolve your issue but its worth a shot.
That worked! Thank you! I wouldn't of guessed that was the solution. :D

---

### Post by SunnyRabbiera on 2009-05-16
> **Dr.Vista said:**
> That worked! Thank you! I wouldn't of guessed that was the solution. :D

Neat, but for future reference dont rely on add/remove all the time, sometimes it messes things up.
A better way to install packages is to use synaptic package manager located under system > administration > Synaptic package manager.
Synaptic is similar to add/remove but is more advanced in its selection and installation methods.
It should be easy enough to use even for the beginner.
Heres something to help:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

