---
title: "windows and linux network"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by kobix on 2005-08-10
Hi

I have two machines. One linux (ubuntu live) and one windows XP. There are connected using a router (WRT54). I want to copy files from the ubuntu to the windows. How do I set up the network. Assume I know nothing.

Thanks.

---

### Post by Whatsisname on 2005-08-10
Assuming that both are connected and can see the internet, I think the easiest solution would be to use SCP to copy stuff. You can get winscp for free online (open source) and ubuntu should have scp built in. No network configuration required.

---

### Post by kobix on 2005-08-10
:) 
Thanks. Still, is there is a way to set a network?

Thanks, Koby

---

### Post by cwaldbieser on 2005-08-10
[QUOTE=kobix]:) 
Thanks. Still, is there is a way to set a network?

Thanks, Koby[/QUOTE]
You will probably have to elaborate on what you mean by "set a network".  Try describing in detail what you want to be able to do.  Drag and drop file sharing?  Remote control?  Server web-pages?  There are many possibilities.

---

### Post by kobix on 2005-08-10
Thanks. I mean that I can see a defined portion of the hard disk of the other machine. And have the ability to copy from one filesystem to the other. Later I would like to open a terminal on one machine  using the other (e.g. open a terminal on the linux machine using cygwin on the windows machine).

Thanks

---

### Post by az on 2005-08-10
[QUOTE=kobix]Thanks. I mean that I can see a defined portion of the hard disk of the other machine. And have the ability to copy from one filesystem to the other. Later I would like to open a terminal on one machine  using the other (e.g. open a terminal on the linux machine using cygwin on the windows machine).

Thanks[/QUOTE]
Click on System - Administration-Shared folders.


It will tell you to install samba or nfs.  Install samba using synaptic.

Go back to the shared folders GUI and Share your folder.  Give it a name.

Go to your windows machine and look at your shared network folders.  You should see your ubuntu box's shared folders.

---

### Post by kobix on 2005-08-10
Thanks. How do I know the name of the machine running linux? and its ip address?

Thanks.

---

### Post by cwaldbieser on 2005-08-11
[QUOTE=kobix]Thanks. How do I know the name of the machine running linux? and its ip address?

Thanks.[/QUOTE]
Open the terminal on Ubuntu.  type "ifconfig".  This command should show you the IP address for each network card.  The "hostname" command should tell you the computer's name.

---

### Post by kobix on 2005-08-11
Thanks.
Is there is a way to mount the destination shared folder of Windows?

Thanks, Koby

---

### Post by kobix on 2005-08-11
The samba does not work. The windows cant see it.

Thanks.

---

### Post by varunus on 2005-08-11
Can you see windows shares from Ubuntu?  Open up your network servers (Places->Network Servers).  Do you see the windows machine's shared folders?  (They need to be shared by right clicking and sharing them, the ubuntu box will make you log on to your windows machine.)

Do you have a firewall installed?  If not, Ubuntu blocks most ports by default and keeps a very restrictive firewall up automatically.  Get "firestarter" from synaptic on the Ubuntu machine.  Once you do, open it up (its in system tools under applications), and go through the wizard.  Default settings should be ok.  Once its open, go over to policy, right click under the allow service area, choose to add a rule.  Allow the samba ports through.

---

### Post by kobix on 2005-08-11
Now I cant even see the linux machine from windows. Furthermore, when I try to map-a-network-drive on the ubuntu machine I asked for a password and a login. I tried few things but nothing works.

When I share the folders using the smb should I set the machine to be WINS server?

Thanks

---

### Post by kobix on 2005-08-11
without the firewall I CAN see the linux machine, but not the shared folders. When I try to map-a-drive to them manually I am aksed for a password.

Thanks.

---

