---
title: "computer won't update"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by christafo on 2010-07-24
Hey,

im constantly seeing the update required icon in the gnome panel (red icon, exclamation mark in a triangle). i click to check for updates and get this error message.


"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

What can i do to solve this?

My computer is connected to the internet via wifi, and everything is working fine (im posting this thread on the computer itself).

Thanks in advance

x

---

### Post by christafo on 2010-07-24
Here's a screenshot of the error window if that helps at all.

---

### Post by beeny on 2010-07-24
Maybe the server you've chosen to fetch main repositories from is down.

Try doing System->Administration->Synaptic Packet Manager

Then do Setting->Repositories and on the tab that you see find out which server you can use by selecting different ones and issuing reload in the main Synaptic window until you find one that Synaptic doesn't complain about.

If this works maybe an update windows pops up. If it doesn't do System->Administration->Update Manager.

---

### Post by PPPilot on 2010-07-24
From time to time, some of the update sites are off line for updating and maintenance etc. I would not be to worried as I see this from time to time. I clicked on the ppa link you posted and got a 404 error so it would seem the site is down and it is not a problem on your end. In another day or so the site should be up and you will loose the error. If for some reason it does not go away, you can # (comment) that line out in your software sources list.

---

### Post by aidenscool09 on 2010-07-24
have you tried removing it from your sources?

---

### Post by wojox on 2010-07-24
> **christafo said:**
> Hey,

im constantly seeing the update required icon in the gnome panel (red icon, exclamation mark in a triangle). i click to check for updates and get this error message.


"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

What can i do to solve this?

My computer is connected to the internet via wifi, and everything is working fine (im posting this thread on the computer itself).

Thanks in advance

x

Try

```
gksudo gedit /etc/apt/sources.list
```

See if you can find that line in the file and comment it out with a pound sign (#).

---

### Post by PPPilot on 2010-07-24
You probably will not find your ppa in the sources.list file. Each of these ppa files has there own list file. I am not sure what the name of the list file you have here so using gedit will be difficult. I would suggest that you go here: [HTML]http://ubuntu-tweak.com/[/HTML]You can download the Ubuntu-Tweak deb file that you can just click on the file to install. After you get Ubuntu-Tweak up, on the left side under Applications, select Source Editor. In the right hand window you will see your sources.list file. Below this window on the left you will see a button that says sources.list with up/down arrows next to it. Click on the arrows and you will then see any other list files that you have. Select the one you need and it will appear in the edit window. Then select the Unlock button on the Right. Enter your password and edit as required. Then quit and your changes will be saved. By the way, Ubuntu-Tweak does all manner of other neat stuff so go through the whole thing....

---

### Post by CharlesA on 2010-07-24
If it's a PPA and it's added the way I think it is.

Try this:

```
ls /etc/apt/sources.list.d/
```

See if there is anything in there.

---

### Post by k3lt01 on 2010-07-24
> **PPPilot said:**
> You probably will not find your ppa in the sources.list file. Each of these ppa files has there own list file. I am not sure what the name of the list file you have here so using gedit will be difficult. I would suggest that you go here: [HTML]http://ubuntu-tweak.com/[/HTML]You can download the Ubuntu-Tweak deb file that you can just click on the file to install. After you get Ubuntu-Tweak up, on the left side under Applications, select Source Editor. In the right hand window you will see your sources.list file. Below this window on the left you will see a button that says sources.list with up/down arrows next to it. Click on the arrows and you will then see any other list files that you have. Select the one you need and it will appear in the edit window. Then select the Unlock button on the Right. Enter your password and edit as required. Then quit and your changes will be saved. By the way, Ubuntu-Tweak does all manner of other neat stuff so go through the whole thing....

Hmmm. PPAs are in the source list file if update manager is getting an error because of it. Ubuntu Tweak will not help with this as it is not an UT issue rather it will most probably be a server down issue.

---

