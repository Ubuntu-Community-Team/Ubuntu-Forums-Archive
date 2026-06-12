---
title: "general help, scripts, servers, VM and such"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by kirior on 2011-04-20
Hi everyone

Sorry in advance if double posted or such. 
I just got a windows on my VirtualMachine and would like to know how yo edit/add/write script that would associate data between VirtualMachine and my Ubuntu on startup. 
Second thing is another script to start and open my terminal window on startup. 
Another thing is that I got xfce GUI and would like to use this one over gnome but every time I boot my PC it always go to gnome. Should I just generally remove gnome or there is other way to do so.
Last is that I would like to setup server between my Ubuntu and any other distro on VirtualMachine. How to do it?
I would like to state that I am n00b in Linux and Ubuntu, got it for about a week.
Where I can as well find a tutorial on how to start with shell scripts.

Thank you everyone in advance for any help/links/tutorials/general directions where to find answers.

Regards

---

### Post by kirior on 2011-04-21
I am just replying to bring my post to the first page so more people could see it.

Sorry if that's against rules or such.

Tux for any help.

---

### Post by daweefolk on 2011-04-21
> **kirior said:**
> I just got a windows on my VirtualMachine and would like to know how yo edit/add/write script that would associate data between VirtualMachine and my Ubuntu on startup. 

If you're using VirtualBox, there should be an option to specify a shared folder. 
> **kirior said:**
> 
Another thing is that I got xfce GUI and would like to use this one over gnome but every time I boot my PC it always go to gnome. Should I just generally remove gnome or there is other way to do so.
In XDM/GDM/whatever login manager you have, you can set what session type you want. choose xfce and next time you log in just choose 'last session'.
> **kirior said:**
> 
Where I can as well find a tutorial on how to start with shell scripts.
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
It may look overwhelming at first, but it just breaks up a lot of the information into separate pages
I can't answer all your questions, but this is a start

---

### Post by kirior on 2011-04-22
HI

Thx for reply. 
The Login session i finally found where to change it so this is cool :). 
About Virtual Machine there is a option to set shared folders but as well they give you a command 'mount -t vboxsf share mount_point' so does that mean that the 'mount_point' is the shared folder i specified and that line i would like to add to like startup script so i don't have to do it manually every time.
So now just the server question left. 

Thank you all in advance for help.

Regards

---

### Post by kirior on 2011-04-22
below solved, i just created a new folder in my home directory and added it to my shared folders on VM. working now


ok so now i got to the point where i wanthed to set up a shared folder on my virtual box using this method
**Prepare host**

 On the host (ubuntu) computer, run 
mkdir ~/VirtualBoxShare
VBoxManage sharedfolder add "XP" -name "share" -hostpath /home/your/shared/folder/VirtualBoxShare/Where "XP" is the name of the virtual machine in [VirtualBox]("https://help.ubuntu.com/community/VirtualBox"), and "share" is the name of the share as the guest machine will see it. The hostpath must be a fully-qualified path. 

the mkdir part worked perfect but than i got some errors:
root@marek-desktop:/home/marek# VBoxManage sharedfolder add "Win7" --name "share" --hostpath /home/marek/VirtualBox\ VMs/
VBoxManage: error: Could not find a registered machine named 'Win7'
VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component VirtualBox, interface IVirtualBox, callee nsISupports
Context: "FindMachine(Bstr(a->argv[1]).raw(), machine.asOutParam())" at line 648 of file VBoxManageMisc.cpp
dunno that to do or how to solve this.

---

