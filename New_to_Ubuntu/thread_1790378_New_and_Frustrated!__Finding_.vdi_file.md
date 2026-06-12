---
title: "New and Frustrated!  Finding .vdi file"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by sallykwitt on 2011-06-24
Hi,

I am really new to all of this, so don't judge me!

I installed a virtualbox windowsxp just to run netflix online.  Even though I gave it 50 GB disk space and 1024MB RAM, it was so irritatingly slow.  I deleted it, and uninstalled the Virtual Box program.  I can't find the .vdi file that everyone talks about.

I really want to be able to watch netflix programs while I work online or play games, but I see now that it is not practial since I installed a new hard drive and have committed to Ubuntu.

How do I get rid of the file that is defining the virtual drive?  I need baby step instructions, please!  All the answers in the forums and blogs make it sound so easy, and I just can't find it.

Thank you,

Sally

---

### Post by jtarin on 2011-06-25
We'll use the locate command to find it:
Open a terminal and type ```
sudo updatedb
```it will take a few moments to run....when it returns to the prompt type ```
locate .vdi
```it will then show you all instances of .vdi on your computer. You can then navigate to them and remove. If there is still some dificulty post back.

---

### Post by sallykwitt on 2011-06-25
I got through the sugo updatedb ok, then put in locate .vdi but it didn'e come back with anything except the regular prompt.

The hard drive is 160 GB, and I have 5 GB used on it in Ubuntu and files.  It is showing 118GB available, so it is still hiding the 50 GB that I reserved for my failed experiment with the virtual xp machine.

Thenk you for your patience!

Sally

---

### Post by slooksterpsv on 2011-06-25
> **sallykwitt said:**
> I got through the sugo updatedb ok, then put in locate .vdi but it didn'e come back with anything except the regular prompt.

The hard drive is 160 GB, and I have 5 GB used on it in Ubuntu and files.  It is showing 118GB available, so it is still hiding the 50 GB that I reserved for my failed experiment with the virtual xp machine.

Thenk you for your patience!

Sally

If it's VirtualBox 4.0 or higher it's located in:
/home/<youruser>/VirtualBox/<vm name>
If it's VirtualBox 3.xx or lower it's located in:
/home/<youruser>/.VirtualBox/<vm name>

Notice on 3.x it's .VirtualBox (see the DOT in front of it) =D.

---

### Post by sallykwitt on 2011-06-25
Thanks for your help.

WHERE do I go to find /home/<youruser>/VirtualBox/<vm name>??

Will it be there after uninstalling virtualbox anyway?

It is just not intuitive to me to find files on ubuntu.  

I know I am going to feel stupid when it is all sorted!

Appreciate it,

Sally

---

### Post by tgm4883 on 2011-06-25
> **sallykwitt said:**
> Thanks for your help.

WHERE do I go to find /home/<youruser>/VirtualBox/<vm name>??

Will it be there after uninstalling virtualbox anyway?

It is just not intuitive to me to find files on ubuntu.  

I know I am going to feel stupid when it is all sorted!

Appreciate it,

Sally

Open a file browser such as Nautilus. If it's the old style then you may need to view hidden files (CTRL+h). The folder will not be removed by removing VirtualBox.

Also note that you may need to empty your recycle bin

---

### Post by slooksterpsv on 2011-06-25
> **sallykwitt said:**
> Thanks for your help.

WHERE do I go to find /home/<youruser>/VirtualBox/<vm name>??

Will it be there after uninstalling virtualbox anyway?

It is just not intuitive to me to find files on ubuntu.  

I know I am going to feel stupid when it is all sorted!

Appreciate it,

Sally

I'm so sorry, that was my bad, your name is what you login with, so if when you installed your user you named sally you'd go to /home/sally
and if the VM name was: Windows XP it'd be:

/home/sally/VirtualBox/Windows XP/

Which you would get to by going to Dash -> type in: nautilus -> click on Nautilus -> double-click on VirtualBox then double-click on Windows XP and the VDI should be there, if it is delete it and empty your trash bin.

I apologize, I type without thinking some days; like windows puts your files in: C:\Users\<your name>\Documents or what not where yourname may be "Sally" or that.

---

### Post by nzjethro on 2011-06-25
Two ways - the GUI way and the command line way.

To get there via command line, type
```
cd ~/VirtualBox/<vmname>
```

The if you run

```
ls
```

it will show you all the files in that directory. Find the one you need to delete, and type

```
sudo rm <filename>
```


Els, to go via GUI, open your file manager (just like "My Computer" in Windows), then navigate to that folder. If it's hidden, press ctrl + h to show hidden folders. Then right click the file, and select Delete.

Depending on permissions for the file, the GUI way may not work.

---

### Post by jtarin on 2011-06-25
> **sallykwitt said:**
> I got through the sugo updatedb ok, then put in locate .vdi but it didn'e come back with anything except the regular prompt.

The hard drive is 160 GB, and I have 5 GB used on it in Ubuntu and files.  It is showing 118GB available, so it is still hiding the 50 GB that I reserved for my failed experiment with the virtual xp machine.

Thenk you for your patience!

SallyPossibly a typo when you posted, but in case.
It's "sudo updatedb" not "sugo updatedb"

You were given the option at installation where you wanted to place the file....do you remember?

---

### Post by ClientAlive on 2011-06-25
I have a couple questions for you if that's ok.

1> What is wrong with using a windows virtual machine to watch netflix? I mean, why isn't it working for you and why do you want to just say forget it? Have you tried to fix that so you can use the thing the way you wanted to in the first place?

2> What distribution and release of Ubuntu are you using?

If you are using Ubuntu 10.04 you can click "Places" in the menu bar across the top of your desktop then click "Home Folder." If you are using Virtual Box 4.0 or later the default folder where the virtual machine is stored is named "VirtualBox VMs" you will find several files in there that make up your virtual machine. One of them will have the .vdi extension at the end of the name but there is more than one thing that makes up that virtual machine.

If you are using Ubuntu 11.04 the navigation is a bit different. I used to run 11.04 but it's been a while. I'm pretty sure the home folder is accessed through an icon on the vertical bar along the left side of the desktop.

If what you really want is to completely remove the virtual machine there is a much easier way to do that. Launch Virtual Box and then right click the virtual machine listed in the pane on the left. In the menu that appears you will see an option called "remove," when you click that a window will appear and have three buttons along the bottom of it. One of them says "Delete all files." If you click that button it will completely remove the virtual machine (all of it).

If you want to uninstall Virtual Box you can locate the program called "Synaptic Package Manager" on your system. You'll be asked to enter your password before it will launch. When you get it running you can type virtual box in the search field and hit enter. Somewhere in that list you will see it listed; and, if it's an installed program, it will have a solid green box (a little one) to the left of the listing. You can right click the listing and select "mark for removal" or "mark for complete removal" and then click "apply" button on the toolbar across the top of the program.


All that being said, I would like to strongly encourage you, no, urge you - to keep Virtual Box and learn to use it. Virtual Box is one of the coolest things I've ever messed with. Did you know I just made an exact duplicate of my operating system in virtual box? It's a little mini replica and I can use it to test out anything I'm not sure of before I try it on my actual system. Keeps me out of trouble so I don't do something I'd regret later. I can use it to practice and learn more advanced stuff too and not worry about hurting my real system if I make a mistake. And what about the fact that you can load it up with all kinds of different operating systems and just play? Maybe not everyone is like me but I think that's the cat's meow right there.

:D

---

