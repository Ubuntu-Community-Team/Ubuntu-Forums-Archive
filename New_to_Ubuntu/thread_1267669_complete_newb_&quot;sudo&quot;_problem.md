---
title: "complete newb &quot;sudo&quot; problem"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by cutoffmyfireman on 2009-09-16
first ten minutes ever using linux so give me a break here, lol. trying to install flash. and I get this error

"failed to run /usr/sbin/synaptic =hid main window= non interactive 'set selections file'. /tmp/tmpLlbLGS as user root. the underlying authorize mechanism (sudo)          does not allow to run this program."

wtf. basically says i need the administrators permission, but thats what I am. help? 

thanks in advanced for leveling with me, and feel free to poke fun as long as you solve the problem, ha.

---

### Post by pastalavista on 2009-09-16
How were you trying to install flash? What application prompted that error message?

---

### Post by stumbleUpon on 2009-09-16
Welcome to Ubuntu..!!

If you are the only user on your machine, then your password is also the root password. Thus when you need to perform some tasks that require administrative privileges, then you can use your own password.

This and many other details are explained in the freely available book here

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

Regarding installation of packages, you need to use synaptic and this also requires administrative privileges (which means again the same password as yours). See here for more info on this

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by zeroseven0183 on 2009-09-16
I think what it's saying is that you run the command with **sudo**. Did you include **sudo **before the command (assuming it's executed in the Terminal).

You can also download the Flash Player in the [Download site of Adobe]("http://get.adobe.com/flashplayer/"). Just select .deb in the dropdown box for Ubuntu. Once downloaded, you will be asked for the root password.

By the way, welcome to the Forums!

---

### Post by cutoffmyfireman on 2009-09-16
i appreciate the quick replies, and yeah I'm using the password I logged in with. 

...maybe I don't have administrative privileges, but this is the only account on the computer. hmmm

---

### Post by cutoffmyfireman on 2009-09-16
I tried to upload a screencap of the error, but 250free is saying it doesnt have a name. wtffff.

oh cruel fate, why have you bestowed this ignorance of linux upon me?

I must not be the admin right? thats the only thing that makes sense to me.

---

### Post by Geoff918 on 2009-09-16
Methinks you are doing this the hard way in some way shape or form. My advice is the following:

Go to Applications
Drop down to Add/Remove
Search for "Ubuntu Restricted Extras"
This will install flash-nonfree, etc. for you as well as some other things you may desire. I believe it also includes MP3 support, Java, etc.

---

### Post by Paqman on 2009-09-16
+1 for ubuntu-restricted-extras

cutoffmyfireman: You'll find that installing software on Linux is different from on Windows. But here's the good news: it's a lot easier and safer!

On Windows you have to search for the software yourself, find some site, figure out if it's trustworthy, download yourself, then manually run the installer, then find whatever random name it's installed into your menus as. Then good luck trying to keep it updated!

On Linux all you need to do is open your package manager, search for the name, tick and "apply". Done! And it'll automatically update itself, which is (IMO) awesome.

The basic package manager is at Applications > Add/Remove, and there's a more comprehensive one at System > Admin > Synaptic Package Manager.

---

