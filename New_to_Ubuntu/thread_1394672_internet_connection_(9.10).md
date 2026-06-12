---
title: "internet connection (9.10)"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by zery on 2010-01-30
Hi All,

I'm a new user in linux, right now i'm using Ubuntu 9.10, i've got a few question:

1. i'm using huawei 160g modem and use GSM as carrier to connect to internet,i've managed to connect using wvdial command, but i never able to connect using Gnome Network Manager, i have tried evrything in tutorial found in the net, but it still can't connect, any help??

2. How to make a launcher on my desktop so i will not keep detecting my modem from the terminal, i'm hoping by using that shortcuts i can detect my modem and connect at once??

3. How can i know the volume of my quota had been used??

Sorry for so much question, any help would be apreciated.

---

### Post by think13 on 2010-01-30
2) If you can connect using only the wvdial command, you could make the launcher simply execute that command, by right clicking on the desktop and selecting "Create Launcher". Then you can change the type to "Application in Terminal", and use the wvdial command.

If you need to execute more than one command, you could write a shell script to run those commands, and have the launcher run the script. (Here's an introduction to shell scripting you might find useful: [http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)).

I'm not sure about your other questions, sorry.

---

### Post by zery on 2010-01-30
> **think13 said:**
> 2) If you can connect using only the wvdial command, you could make the launcher simply execute that command, by right clicking on the desktop and selecting "Create Launcher". Then you can change the type to "Application in Terminal", and use the wvdial command.

If you need to execute more than one command, you could write a shell script to run those commands, and have the launcher run the script. (Here's an introduction to shell scripting you might find useful: [http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)).

I'm not sure about your other questions, sorry.

thaks for your reply, i'll try it soon, i'm still witing for another help on my other question.

cheers

---

### Post by cbabbage on 2010-01-31
I have a huawei e169, which when I updated to 9.10. didn't work anymore. Apparently there was a bug affecting some of the huawei modems in one of the kernels. Following someone's advice from another forum, I managed to get connected to the internet using a terminal and then, updated to the latest kernel. This fixed the problem just fine.

---

### Post by zery on 2010-01-31
> **cbabbage said:**
> I have a huawei e169, which when I updated to 9.10. didn't work anymore. Apparently there was a bug affecting some of the huawei modems in one of the kernels. Following someone's advice from another forum, I managed to get connected to the internet using a terminal and then, updated to the latest kernel. This fixed the problem just fine.

sure this would lead me to anther question, i dont know how to update a kernel??

cheers

---

### Post by cbabbage on 2010-01-31
Updating the kernel, or any other software - the easiest way is use the Update Manager. You'll find it under System > Administration > Update Manager. Select it and enter your password. It will then list all the available updates, including any new kernels.

You might find, if you haven't used it before, that there are a lot of updates available. Simplest thing is to just click install and let the Manager install all the updates, but this is not essential - you can pick and choose which updates to install. If you install everything it may be a large download and take a long time. If you go through and just select the packages which start with linux- ie linux-headers, linux-kernel, you will be getting the latest kernel.

Once you've selected which updates you want, just click install and it will download and install everything, including all dependencies, without you having to do anything.

If you install a new kernel, you will need to restart the computer before using it.

I hope this helps.

---

### Post by zery on 2010-01-31
> **cbabbage said:**
> Updating the kernel, or any other software - the easiest way is use the Update Manager. You'll find it under System > Administration > Update Manager. Select it and enter your password. It will then list all the available updates, including any new kernels.

You might find, if you haven't used it before, that there are a lot of updates available. Simplest thing is to just click install and let the Manager install all the updates, but this is not essential - you can pick and choose which updates to install. If you install everything it may be a large download and take a long time. If you go through and just select the packages which start with linux- ie linux-headers, linux-kernel, you will be getting the latest kernel.

Once you've selected which updates you want, just click install and it will download and install everything, including all dependencies, without you having to do anything.

If you install a new kernel, you will need to restart the computer before using it.

I hope this helps.

thank you, i'm on it right now.

---

### Post by soloman498 on 2010-01-31
Answer to Q3,if you use Firefox it has an add on called net usage which after setting up connects to your isp and gets all the info for you.

---

### Post by 3rdalbum on 2010-01-31
1. Update to the Lucid development branch - I believe they've got the modems fixed now. I can connect first time, every time now.

3. Your ISP's website will have an area you can log into to check your quota. You can use Prism to put this data on your desktop as though it was another program.

---

### Post by zery on 2010-01-31
thank you guys, i'll give it a try and post the result soon.

---

### Post by J V on 2010-01-31
> **think13 said:**
> 2) If you can connect using only the wvdial command, you could make the launcher simply execute that command, by right clicking on the desktop and selecting "Create Launcher". Then you can change the type to "Application in Terminal", and use the wvdial command.

If you need to execute more than one command, you could write a shell script to run those commands, and have the launcher run the script. (Here's an introduction to shell scripting you might find useful: [http://steve-parker.org/sh/sh.shtml](http://steve-parker.org/sh/sh.shtml)).

I'm not sure about your other questions, sorry.Better yet, add the command to startup programs and it will automatically connect when you log in...

---

