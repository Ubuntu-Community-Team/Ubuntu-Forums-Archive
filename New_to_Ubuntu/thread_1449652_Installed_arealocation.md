---
title: "Installed area/location?"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by sanjaypothen on 2010-04-08
I have installed the documentation of clam av,But i don't know the loction it downloaded.How  do i find it? The synaptic package manager shows as installed.

---

### Post by mcduck on 2010-04-08
Take a look in /usr/share/doc, that's the standard location for all documentation files.

---

### Post by sanjaypothen on 2010-04-08
Where should i type this?

---

### Post by mcduck on 2010-04-08
> **sanjaypothen said:**
> Where should i type this?

It's not something you should type anywhere, it's the location where the document files are on your hard drive. Just use your file manager to get there.

---

### Post by 3rdalbum on 2010-04-08
You can always find the location of the files installed by a package.

In Synaptic, find the package, and then right-click it and go to Properties. Click on "Installed Files" and it'll show you the location; which is likely to be somewhere in (Filesystem)/usr/share/doc

---

### Post by sanjaypothen on 2010-04-08
Good! thanks, 3rdalbum. I have found the installed document files of clamav;But how to open it and read it?

---

### Post by sanjaypothen on 2010-04-08
Sorry,may i know what is file manager? how do i get there?

---

### Post by warfacegod on 2010-04-08
Your file manager is what allows you to wander through your files and folders. If you open say, your Home folder, you've used your file manager.

---

### Post by sanjaypothen on 2010-04-08
I have gone to the file manager and found the installed documentation of clamav-doc files in the (filessystem)/usr/share/doc but i want to read it all, how do i read the documents, as i read a document about a program or a package? I want to read this clamav document as you read a document in the ubuntu forum or community,that is why i have downloaded it.Even double clicking it is not readable.It is only opening to new windows, with sometimes small images or some commands like in notepad of windows os.


Can anybody answer my doubt pl.?

---

### Post by mcduck on 2010-04-08
> **sanjaypothen said:**
> I have gone to the file manager and found the installed documentation of clamav-doc files in the (filessystem)/usr/share/doc but i want to read it all, how do i read the documents, as i read a document about a program or a package? I want to read this clamav document as you read a document in the ubuntu forum or community,that is why i have downloaded it.Even double clicking it is not readable.It is only opening to new windows, with sometimes small images or some commands like in notepad of windows os.

What type of file it is? That's what tells you what program to use to read it...

Also Gnome's Help viewer might show the documentation, try searching for it there, or look in *Advanced Topics->GNU Info pages* or *Advanced Topics->Terminal Commands References*.

---

### Post by sanjaypothen on 2010-04-08
clamav-doc. It the documentation of clamav

---

### Post by mcduck on 2010-04-08
> **sanjaypothen said:**
> clamav-doc. It the documentation of clamav

try running "file clamav-doc" in the same directory where the file is located. That should tell you if it's a text file or something else.

In reality such documentation file isn't really likely to be anything more special than a simple text file, or if you are very lucky then perhaps a .html file. Also all the documentation for ClamAV should be available on their web site in .PDF form...

---

### Post by sanjaypothen on 2010-04-08
Well i don't understand how do i "run" it. The file is in my home folder, filesystem.? Can't find 'run' as in the start menu of windows.

---

### Post by warfacegod on 2010-04-08
Have you tried looking under Help in clamav? It is my understanding that app documentation is readable from the program it is for.

---

### Post by sanjaypothen on 2010-04-08
I have installed the clamav-doc and clam daemon from the synaptic package manager, the file have been intalled for sure 100% ,but i cannot activate it,since the document is not readable.I have a feeling that the clamav -dameon is working in the background,it is not confirmed.Now how to read it(document) and the activation of clamav -dameon is confusing.

---

### Post by warfacegod on 2010-04-08
Open a Terminal and type: clamav

If that doesn't do anything try typing in the name of the documentation package.

---

### Post by sanjaypothen on 2010-04-09
Typed "clamav" in the terminal and i got the output as 

No command "clamav" found

When typed the name of the package i got the output as

clamav-docs-command not found

when typed clamav-daemon the output got was

clamav-daemon-command not found

---

### Post by warfacegod on 2010-04-09
Have you installed clamav itself? If not, then do so. Easiest way is to use Synaptic under System> Admin.

---

### Post by sanjaypothen on 2010-04-09
> **warfacegod said:**
> Have you installed clamav itself? If not, then do so. Easiest way is to use Synaptic under System> Admin.
Yes already! two packages have been installed.(1) calmav-daemon and it dependencies(2)clamav-docs.

---

### Post by warfacegod on 2010-04-09
Install clamtk. It will give you a graphical interface for clamav and should put clamav into your Applications menu. You should then be able to read the documentation.

```
sudo apt-get install clamtk
```

---

### Post by mechro on 2010-04-09
Clamav docs are accessible from a Terminal with the **man** command. There isn't actually a **clamav** command so try **man clamscan**.

You can get a clamav graphical front-end if you install **clamtk**.

This wiki may help...

[http://wiki.clamav.net/Main/WebHome](http://wiki.clamav.net/Main/WebHome)

---

### Post by sanjaypothen on 2010-04-09
See (clamtk) is universe.I don't want that.My basic problem is to read the downloaded clamav-docs documentation package and also to acivate (if not activated) the other package clamav-daemon

---

### Post by mechro on 2010-04-09
Go to **Places > Home**

You are now in the Nautilus file manager...

Click the Up button twice...

You are now in the root folder...

Double-click through the following folders...

[B]usr

share

doc

clamav-docs

html[/B]

Double click the index.html file and it should open the Firefox browser with all the clamav docs at your fingertips.

---

### Post by sanjaypothen on 2010-04-09
> **mechro said:**
> Go to **Places > Home**

You are now in the Nautilus file manager...

Click the Up button twice...

You are now in the root folder...

Double-click through the following folders...

[B]usr

share

doc

clamav-docs







html[/B]

Double click the index.html file and it should open the Firefox browser with all the clamav docs at your fingertips.

Thank you!! i got the clamav-docs documentation.
     
  Is this the normal method to open clamav-docs? it has to be opened with many clicks.Can it be opened one or two clicks from "desktop" or "application menu" or simply from somewhere with one or two clicks.

   Next i want to activate the clamav-daemon.The documentation is not that friendly.

    Can some one guide me to activate clamav-daemon so as to scan my system.Or is it working in the background? How do i know its status?

---

### Post by mechro on 2010-04-09
> **sanjaypothen said:**
> Thank you!! i got the clamav-docs documentation.
     
  Is this the normal method to open clamav-docs? it has to be opened with many clicks.Can it be opened one or two clicks from "desktop" or "application menu" or simply from somewhere with one or two clicks.

   Next i want to activate the clamav-daemon.The documentation is not that friendly.

    Can some one guide me to activate clamav-daemon so as to scan my system.Or is it working in the background? How do i know its status?

Hmm... Clamav doesn't have a graphical front-end with the docs integrated into it so I'm afraid you'll have to make your own shortcut. One option is to make a Bookmark in the Nautilus file manager... navigate to /usr/share/doc/clamav-docs and then **Bookmarks > Add Bookmark**

The clamav daemon should be running once you've installed it or it will be after a reboot. If you look in **System > Administration > System Monitor** you should see clamd (the daemon) listed as running/sleeping under All Processes.

A better graphical front-end for clamav is **klamav** but it would mean you'd also have to install a lot of KDE desktop dependencies... Synaptic will do this for you automatically and it will run in your normal Gnome desktop, but bear in mind it will install quite a lot of stuff to get a functioning KDE environment.

---

### Post by sanjaypothen on 2010-04-09
Well,i have installed the clamav-daemon from the synaptic package manager; the properties section in the menu showes the installed file.But clamd is not shown in the system>administration>system moniter,listed as sleeping/running under" All Process" Pl.i do not want to install klamav,it is not supported by canonical.

---

### Post by mechro on 2010-04-09
In a Terminal run this command...

```
sudo service clamav-daemon status
```

If it says it isn't running then do...

```
sudo service clamav-daemon start
```

---

### Post by sanjaypothen on 2010-04-09
> **mechro said:**
> In a Terminal run this command...

```
sudo service clamav-daemon status
```If it says it isn't running then do...

```
sudo service clamav-daemon start
```


Thank you!!! When typed in the terminal,the status says as running. But the processes list in the system moniter is not showing clamd, is any thing wrong.?

---

### Post by mechro on 2010-04-09
> **sanjaypothen said:**
> Thank you!!! When typed in the terminal,the status says as running. But the processes list in the system moniter is not showing is any thing wrong.?

In the System Monitor click the **Processes Tab** and click **View > All Processes**. **clamd** should be in there somewhere.

---

### Post by sanjaypothen on 2010-04-10
> **mechro said:**
> In the System Monitor click the **Processes Tab** and click **View > All Processes**. **clamd** should be in there somewhere.
Yes!!! thank uvery much!! It is there.

---

