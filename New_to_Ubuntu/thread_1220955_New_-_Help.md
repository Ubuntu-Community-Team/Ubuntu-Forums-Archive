---
title: "New - Help"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by snitchard on 2009-07-23
Hello,

I downloaded KUbuntu yesterday and instaled it on a virtual machine using Virtual Box and it works great.  The problem is I have no clue how to use KUbuntu.  I have been trying to learn Linux for a while now and always stop after the initial OS install.  I'm a Windows user so that doesn't help matters much.  I have a tendancy to be impatient too.  Where do I begin???  I want to join the domain here at work and be able to print and access network shares.  Everything is Windows based though.  Also I want to learn how to find and download and update software on UBuntu.  I'm a computer tech and you'd think that would make it easier but it doesn't.  Any help or advice would be greatly appreciated.

Thanks,
Rich

---

### Post by 3rdalbum on 2009-07-23
> **snitchard said:**
> Hello,

I downloaded KUbuntu yesterday and instaled it on a virtual machine using Virtual Box and it works great.  The problem is I have no clue how to use KUbuntu.  I have been trying to learn Linux for a while now and always stop after the initial OS install.  I'm a Windows user so that doesn't help matters much.  I have a tendancy to be impatient too.  Where do I begin???  I want to join the domain here at work and be able to print and access network shares.  Everything is Windows based though.  Also I want to learn how to find and download and update software on UBuntu.  I'm a computer tech and you'd think that would make it easier but it doesn't.  Any help or advice would be greatly appreciated.

Thanks,
Rich

I can answer the second question, about finding and downloading software for Ubuntu. If you click the K menu, and in the search bar you type "kpackagekit", you will find the default Kubuntu package manager, which will download and install software for you.

You might need to enable some extra repositories in the Software Sources program; I'm not sure if this is available in Kubuntu, but basically you enable the Multiverse and Universe repositories and you'll have access to the whole catalog of Ubuntu software.

Printing and accessing network shares is not something I can advise about; I know how to do it in Gnome, but you're using KDE. The network shares should be accessible from the Dolphin file manager, when you click Network in the left pane (from memory). If the shares don't appear and you know they're not "hidden" shares, then your virtualisation software may be set up incorrectly in terms of network.

EDIT: Changed "adept" to "kpackagekit" - I wasn't aware they had changed in this version.

---

### Post by Sxeptomaniac on 2009-07-23
If you have a newer version of Kubuntu, software installation will not be through Adept, but a different program called Kpackagekit.  Either way, it will allow you to search for and add software pretty easily.

You can even add different package manager interfaces, such as Adept or Gnome's Synaptic from Kpackagekit.  One of the first installations should be the Kubuntu-restricted-extras package, though.  That will enable commonly used formats such as Flash

Edit:  [This guide on switching to Ubuntu from Windows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows) has a lot of information in more detail than we would be able to provide here.  It will help give an overview of the differences.  There's also a page on [working with Windows networks](https://help.ubuntu.com/community/SettingUpSamba).

---

