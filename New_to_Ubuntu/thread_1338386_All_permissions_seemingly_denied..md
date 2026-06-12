---
title: "All permissions seemingly denied."
date: 2009-11-26
forum: New to Ubuntu
---

### Post by zezuza on 2009-11-26
I'm completely new to Ubuntu and linux/unix/open source operating systems/etc. and am having some difficulty getting acclimated. Is this a good place to ask questions? For one thing, I am unable to install any plugins. Permissions are denied. Secondly, drivers give me a similar issue. I'm trying to access my wireless router using wifi, but Ubuntu does not recognise my wireless card though it did when I was using the live CD. Problem is, though, it won't let me install the drivers necessary. Also, when installing Adobe flash, it refuses to do so. When I try to manually move the necessary flash plugin to the proper folder, it also refuses. What gives?

---

### Post by Paqman on 2009-11-26
> **zezuza said:**
> Is this a good place to ask questions?


It certainly is :)

Regarding your wifi drivers, check System > Admin > Hardware drivers and install anything it recommends.

On Ubuntu, we get our software from secure central repositories, not from websites like you do on Windows.

For Flash, go to Applications > Ubuntu Software Centre and search for "restrcited extras" and install it. As for you plugins, plugins for what exactly?

---

### Post by oldos2er on 2009-11-26
You won't be able to install any packages (e.g. Flash) unless you have a working internet connection, which I assume you don't since your wireless isn't working. Which wifi card do you have?

 Anytime you want to install programs or drivers etc., you need to do so as root or admin. See [https://help.ubuntu.com/9.10/add-applications/C/index.html](https://help.ubuntu.com/9.10/add-applications/C/index.html)

---

### Post by mavigozler on 2009-11-26
Check these out:

[https://help.ubuntu.com/community/SoftwareManagement]("https://help.ubuntu.com/community/SoftwareManagement")
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")
[https://help.ubuntu.com/9.10/add-applications/C/index.html]("https://help.ubuntu.com/9.10/add-applications/C/index.html")

Your account should have super-user status.
From the command line (in an terminal:  Applications-->Accessories-->Terminal) it is easy enough to assume super-user status temporarily by putting 'sudo' before any operation that requires administrator level or privileges.

For GUI applications, you may be presented with a window asking for your password to proceed as a super-user.

---

### Post by zezuza on 2009-11-26
> **Paqman said:**
> install anything it recommends.
 
For Flash, go to Applications > Ubuntu Software Centre and search for "restrcited extras" and install it.
 
 Well, yeah, I've tried all that, but it still denies me access to do any of it! As a result, I'm a sad panda.
 
 
 > **oldos2er said:**
> You won't be able to install any packages (e.g. Flash) unless you have a working internet connection, which I assume you don't since your wireless isn't working. Which wifi card do you have?

I can connect to the internet using my wired network, which is how I'm on here in the first place, but even so, I download the required drivers/plugins/etc. Ubuntu tells me it can't find whatever it needs to complete the install or it tells me that I lack permission to do so.

---

### Post by iponeverything on 2009-11-26
Is the account you are using set up with administrative privileges?

Go to System -> Administration ->  Users and Groups to check.

---

### Post by zezuza on 2009-11-26
> **mavigozler said:**
> 
Your account should have super-user status.
From the command line (in an terminal:  Applications-->Accessories-->Terminal) it is easy enough to assume super-user status temporarily by putting 'sudo' before any operation that requires administrator level or privileges.
That doesn't help. I've lurked about for a day and a half before finally making this thread and did all that in terminal to try to get it working, but nonetheless am met with similar issues.

---

### Post by oldos2er on 2009-11-26
> **zezuza said:**
> I can connect to the internet using my wired network, which is how I'm on here in the first place, but even so, I download the required drivers/plugins/etc. Ubuntu tells me it can't find whatever it needs to complete the install or it tells me that I lack permission to do so.

 Are you using terminal commands? If so, can you copy and paste the errors here?

---

### Post by zezuza on 2009-11-26
> **iponeverything said:**
> Is the account you are using set up with administrative privileges?
There are only two accounts: mine and root, and neither of which seem to function as I imagined they should, or am I just wrong?

---

### Post by Don1500 on 2009-11-26
Can you copy your terminal screen when you get rejected please?

You can put the terminal inside some tags and it will look good.

"[c*ode] paste the terminal message [/c*ode]" (Take out the asterisk)

it will look like this

```
paste the terminal message 
```

---

### Post by bodhi.zazen on 2009-11-26
You access system files as root.

Either sudo or gksu (gksu of for graphical aplications)

In a terminal enter :```
sudo -i
```Enter your login password, by default there is no root password.

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by zezuza on 2009-11-26
[IMG]https://post.craigslist.org/imagepreview/n/3n53o43l95O95Pa5S89bqf5baefdc1dfe190b.jpg[/IMG]
Here's something that happens when I try to install flash from within Synaptic.

---

### Post by Don1500 on 2009-11-26
> **zezuza said:**
> [IMG]https://post.craigslist.org/imagepreview/n/3n53o43l95O95Pa5S89bqf5baefdc1dfe190b.jpg[/IMG]
Here's something that happens when I try to install flash from within Synaptic.

Are you online when you do this?

---

### Post by zezuza on 2009-11-26
> **Don1500 said:**
> Can you copy your terminal screen when you get rejected please?
Sure, gimme a minute to find what the hell I was putting in last night! Being so new to this, I've yet to learn all the commands and had just copied what I'd found on other sites.

---

### Post by zezuza on 2009-11-26
> **Don1500 said:**
> Are you online when you do this?
Sure am. I'm using the internet as we speak. I'm posting on here with the very machine that's disallowing me to do stuff.

---

### Post by Don1500 on 2009-11-26
> **zezuza said:**
> Sure am. I'm using the internet as we speak. I'm posting on here with the very machine that's disallowing me to do stuff.

Land line, broadband, or wireless?

---

### Post by oldos2er on 2009-11-26
> **zezuza said:**
> [IMG]https://post.craigslist.org/imagepreview/n/3n53o43l95O95Pa5S89bqf5baefdc1dfe190b.jpg[/IMG]
Here's something that happens when I try to install flash from within Synaptic.

 I can barely make that out. 

 Try running this in a terminal:
```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

---

### Post by zezuza on 2009-11-26
> **Don1500 said:**
> Land line, broadband, or wireless?
I'm connected by ethernet to broadband at the moment. I'm trying to access wireless, but Ubuntu disallows installation of the drivers. Additionally, I'm unable to install plugins as well, which I find odd because everything worked from the live CD. I'm considering switching back to my familiar Windows set up, bugs and all.

---

### Post by MaxIBoy on 2009-11-26
Ubuntu doesn't set a root password, by default you can't actually log in as a root user.

In Ubuntu, by default the first user you created during installation is a "sudoer," meaning this user can use sudo with his/her own password. So login to that user, and add "sudo" to the beginning of any command you need to run as root. Then use your normal password when sudo asks you for one. It looks like you're not typing anything, but that's to stop people knowing how long your password is. 

Use gksudo instead of sudo for graphical programs. So to graphically edit some protected file use "gksudo gedit." You can just use "gksudo gedit" and open the file, or you can do "gksudo gedit /full/path/of/file" or "cd /folder/where/file/is/in ; gksudo gedit file".

If this isn't working then your permissions are likely broken and we can help you fix that. However, since you at least seem able to run synaptic, and that requires root access, it appears that your permissions are behaving perfectly fine.




In general, you will have an easier time installing software from Ubuntu's software repositories (via synaptic,) than you will if you try to download software directly off the internet and install them. Same usually goes for drivers.

Have you tried using the driver manager (which is in the menu or you can run "gksudo jockey-gtk")? If that doesn't work could you tell us what graphic hardware you have? 

If you don't know, could you post what is the output of the command "lspci"?



> **zezuza said:**
> [IMG]https://post.craigslist.org/imagepreview/n/3n53o43l95O95Pa5S89bqf5baefdc1dfe190b.jpg[/IMG]
Here's something that happens when I try to install flash from within Synaptic.
I've had that error before! [This is how I fixed it,]("http://www.linuxquestions.org/questions/debian-26/sid-adobe-flasplugin-is-reinstall-required-but-apt-cant-find-archive-for-it-727572/#post3548726") (loook at  post number six)
Someone else also solved it [this way]("http://www.linuxquestions.org/questions/debian-26/sid-adobe-flasplugin-is-reinstall-required-but-apt-cant-find-archive-for-it-727572/page2.html#post3760191") (post number 26.)

Of course your mileage may vary. And don't actually delete the files, move them to a safe place just in case it doesn't work.

So instead of ```
sudo rm file
```Use```
sudo mv file ~
``` Which moves "mv" the file to your home folder "~".

---

### Post by zezuza on 2009-11-26
> **oldos2er said:**
> I can barely make that out. 

Ah, yeah, sorry about the smallish graphic.

 > **oldos2er said:**
> Try running this in a terminal:
```
sudo apt-get update && sudo apt-get install flashplugin-installer
```
Yeah! That's the command I put in last night! Hold on; here's the error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by MaxIBoy on 2009-11-26
> **zezuza said:**
> ```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```You can't run two package-related programs at the same time. If you were already running synaptic and you try running apt-get, you get that error. Also vice-versa.

This is so one program can't interfere with another, which would cause catastrophic mangling of your packages and configuration.

I personally wish that error message was more useful and informative.

---

### Post by zezuza on 2009-11-26
Guys and Misses, thanks for the help thus far, but the better half just got the call from my mother-in-law that it's about time we head over. She's an older woman and therefore lacks any sort of internet connection there and without wifi access I am unable to leech from a neighbour in the same building. I will be back later in the evening, most likely, to check and revive the thread, if necessary, but my sister-in-law will be there and she may have some insights for me, if not her husband. Thanks again for being such a welcoming community.

---

### Post by egalvan on 2009-11-26
Enjoy Thanksgiving with the family.
The only thing better is Christmas with the family.

and you will find that the "family" here on the forums is quite friendly,
and willing to help.

Cheers

---

