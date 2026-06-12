---
title: "Installing OpenOffice.org 3.0 in Ubuntu 8.10 (Intrepid Ibex)"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by hobo89 on 2008-12-09
OpenOffice 3 was removed from the repositories a while ago, causing us noobies all sorts of problems when looking up how to install it, having to do it from the source. But it is now back so thought I would post a thread as there quite a lot threads about people having problems.

On a side note, OpenOffice 3 is capable of opening MS Office 2007's 'x' formats (*.pptx, *.docx etc), which 2.4 was unable to do. So upgrading to the latest version will save using those online converters and having the formatting of files go crazy.

So to install it from the repositories:

Remove 2.4:
```
sudo apt-get remove $(dpkg -l |grep ^ii|grep openoffice|cut -f3 -d' ')
```

Add the repository:
System > Administration > Synaptic Package Manage > Settings > Repositories > Third Party Software > Add > "deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu" (copy and paste without quotes into the "APT line" box)
Click Close, message box will come up saying something about needing to reload packages, close the message box and click Reload in the top left corner of Synaptic.

Install:
Type in the Quick search box "openoffice", you should now see "openoffice.org" in the list with Latest Version "1:3.0.0-6ubuntu0intrepid1", select the checkbox and "Mark for Installation" It will list other changes it needs to make, such as installing other packages. Click Apply at the top, and confirm any message boxes that pop up and leave it to do it's thing.

You should now have OpenOffice.org 3.0 installed. If, in the menu, clicking the launchers does not work, log out and log back in again and it should be fine.

Any updates will now be automatically applied by the update manager from the repositories. Installing from the source would not have done this.

Hope this helps

---

### Post by gettinoriginal on 2008-12-09
Don't know what I did wrong, but now I cannot access my synaptic package manager.  Can you explain how I fix this ??  See attached for error message

[ATTACH]95789[/ATTACH]

---

### Post by Tatty on 2008-12-09
> **gettinoriginal said:**
> Don't know what I did wrong, but now I cannot access my synaptic package manager.  Can you explain how I fix this ??  See attached for error message

[ATTACH]95789[/ATTACH]

It sounds like you inputted the repository incorrectly.  Double check that.

---

### Post by gettinoriginal on 2008-12-09
Synaptic is totally greyed out, will not let me past the error message.  if I try to close the error message, it closes synaptic.  ](*,)

---

### Post by Tatty on 2008-12-09
> **gettinoriginal said:**
> Synaptic is totally greyed out, will not let me past the error message.  if I try to close the error message, it closes synaptic.  ](*,)

1. Back up your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

2. Edit your sources.list
```
gksu gedit /etc/apt/sources.list
```

The error message says that the problem is on line 59, check to see if it looks right,  If you are not sure then please post the output of ```
cat /etc/apt/sources.list
```

---

### Post by gettinoriginal on 2008-12-09
That solved it, thank you.  Now all I have to figure out is what I did wrong  LOL.

---

### Post by fjf on 2008-12-09
Thanks!.

---

### Post by marcw on 2008-12-09
Why do you say to uninstall 2.4 first?  I've upgraded OOo on 2 different computers (32bit Intrepid laptop; 64bit Intrepid desktop) using the PPA repo and all went fine.  3.0 is now the default and 2.4 is nowhere to be found.

---

### Post by hobo89 on 2008-12-09
> **marcw said:**
> Why do you say to uninstall 2.4 first?  I've upgraded OOo on 2 different computers (32bit Intrepid laptop; 64bit Intrepid desktop) using the PPA repo and all went fine.  3.0 is now the default and 2.4 is nowhere to be found.

Most guides I read said to remove 2.4 first so I included it just to make sure. But thinking about it, that may have just been the guides for installing from the source, as that wouldn't overwrite 2.4 because it is installed from the repositories. 

If someone can confirm whether or not removing 2.4 first might be needed in some cases I will edit the original post.
Thanks.

---

### Post by pdub on 2009-01-14
Thanks for the instructions, worked great. One small correction. The line to add to the repositories should look like this:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

---

### Post by 73ckn797 on 2009-01-14
> **hobo89 said:**
> Most guides I read said to remove 2.4 first so I included it just to make sure. But thinking about it, that may have just been the guides for installing from the source, as that wouldn't overwrite 2.4 because it is installed from the repositories. 

If someone can confirm whether or not removing 2.4 first might be needed in some cases I will edit the original post.
Thanks.

My earlier posts on installing Oo3 were from the Oo download page before Oo3 was available in the repos. Removing 2.4 was necessary at that time. I have since used the repos without having to remove 2.4. I like that it is a perfect fit into Ubuntu with system theme colors and all.

---

