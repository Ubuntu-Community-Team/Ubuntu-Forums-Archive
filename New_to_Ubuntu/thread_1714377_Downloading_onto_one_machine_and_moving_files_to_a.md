---
title: "Downloading onto one machine and moving files to another"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by orrymr on 2011-03-25
Hi all. I'm busy using Maverick on two different machines (with different specs). The one machine has access to very fast internet, while the other doesn't (call the computer with fast internet computer A, and the one without fast internet, Computer B). I've just downloaded Eclipse on Computer A, using the command
```

sudo apt-get install eclipse

```
This seems to have worked. How do I now put the install files say on a USB stick so that I can install it on computer B?

---

### Post by btindie on 2011-03-25
If you look in /var/cache/apt/archives/ you should see the files. To the files from there to the same location on the other machine. I think you should then be able to run apt-get install .... and it'll install from the cache.

---

### Post by orrymr on 2011-03-25
How do I specify that I want to install from cache rather than the net?

---

### Post by tordeu on 2011-03-25
Another thing you could do if you want to install something on the other machine, but not on the one which has the fast internet access, is this:


[LIST=1]
[*]Go to System > Administration > Synaptic Package Manager
[*]Mark all the packages you want for installation
[*]Click on File > "Generate package download script" and save the script (maybe in a separate folder)
[*]Go to the folder where you save saved the script
[*]type ```
sudo ./<scriptname>
```
[*]copy the folder, which now contains all the packages to the other machine
[*]On the other machine, in Synaptic Package Manager, click on "File > Add downloaded Packages" and open the folder which contains the packages
[/LIST]
You can also, as already mentioned, get the packages from /var/cache/apt/archives and then start at point 6.

---

### Post by btindie on 2011-03-25
> **orrymr said:**
> How do I specify that I want to install from cache rather than the net?

You don't have to, it'll automatically see that it's got them in it's cache and install from there instead of downloading them again.

---

### Post by crispy_420 on 2011-03-25
I have to throw this out there but aren't dependencies going to be an issue in all of this? Just worried this could lead to dependency hell where you get one package and it needs another and so on.

Does this other PC not have an internet connection at all?

---

### Post by tordeu on 2011-03-25
I can only say that dependencies are handled correctly with the solution I proposed. There are certainly millions of ways you can somehow achieve this and it really is a matter of choice.
The steps I proposed use Synaptic Package Manager and when you mark a package for installation using Synaptic Package Manager, it will mark all the dependencies for installation, so the download script you can create will also download the dependencies.

The only problem I see with this solution is that dependencies, that you have already installed on the system where you mark the packages for installation, will not get marked for installation (cause they are already installed). BUT, there is a solution to this problem:

Run steps 1-4 on the system where you want the packages to install. Then copy the script to the machine with the fast internet connection and continue with step 5 on this machine.


[LIST]
[*]There are certainly ways to simplify the process. You could keep Synaptic open on the machine with the slow internet connection and then instead of step 7, copy the packages to /var/cache/apt/archives and then hit "Apply" in Synaptic, which should then realize that the packages are mysteriously already there and install from the cache
[*]You could also create a shared folder and save the generated script into this folder. Then you can run the script immediately from the machine with the fast connection and then install the downloaded packages from that shared folder, saving you the need to manually copy the script and packages between the systems.
[/LIST]

---

### Post by orrymr on 2011-03-25
The attached image shows the files which I copied to the /var/cache/apt/archives of the computer with the slow internet. If I now type
```

sudo apt-get install eclipse

```
it shouldn't redownload everything, right? Or am I missing something?

---

### Post by tordeu on 2011-03-25
If these are all the needed archives, it should work without downloading. You could turn your connection off and test it or open System > Administration > System Monitor. Choose the "Resources" Tab. At the bottom it shows you how much data has been sent/received in total, so this should not significantly change during install.

---

### Post by orrymr on 2011-03-26
I think I might have made a mistake with the packages; is there a way I can check to see which packages I'd need for Eclipse (or any other app, for that matter)?

---

### Post by NightwishFan on 2011-03-26
All downloaded packages are in /var/cache/apt/archives. Just use "download only" to get all the packages you need and copy all the .deb files to a flash drive. On the system with a slow net, reload the package sources, and copy all the debs into /var/cache/apt/archives there. Then they will install not needed to download, but you do need correct sources.

---

### Post by tordeu on 2011-03-26
If you want to see the dependencies, than one possibility of doing that in Synaptic Package Manager would be:

[LIST=1]
[*]Right-Click on the package
[*]From the menu, choose "Properties"
[*]Click on the "Dependencies" tab.
[/LIST]

---

### Post by tordeu on 2011-03-26
Oh, just forgot something:

If you already downloaded a .deb package and want to see the dependencies of that, you can call:

```

dpkg-deb -I <package-file>

```

which will list you a lot of infos, including "Depends: ..." which will list the dependencies.

That's another way to do it.

---

