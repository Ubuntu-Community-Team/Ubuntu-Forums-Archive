---
title: "sharing files windows"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by sidprak on 2007-06-15
i am trying to share files between my ubuntu machine and my windows XP machine
i right-clicked the folder and clicked share folder for windows network (samba)

i typed in "\\ip address" in my windows computer on windows explorer and it keeps asking me for a username and password.  I tried my linux password for my account and the root account but it doesnt accept it.

Can someone please help me?

Thanks!

---

### Post by phonixor on 2007-06-15
maby windows password???

also try using computer name
smb://compname/share
for example:
smb://phonixor/D/

---

### Post by lilnovina on 2007-06-16
I have the exact same issue. I created a share on my Ubuntu machine, then from a windows PC i type in:

 \\100.10.3.3\shared


I am then prompted for a username and password. I try both the root and my own login in these formats:

username: LS1\jfritz ,  jfritz@LS1

and then enter my password but nothing works. Does anyone know what credentials it is looking for here?

---

### Post by langi280179 on 2007-06-16
Easy way is to set 

security = share

in /etc/samba/smb.conf

and restart

```

sudo /etc/init.d/samba restart

```

So you won't need to autenticate.

Might be o.k. in a home network but terrible security. 

Better: learn about smbpasswd and it's usage. Should not be to difficult.

---

### Post by doccpu on 2007-06-17
People keep saying do this do that then restart. fine how DO you restart let alone start the smbd and nmbd's in samba?
And in Ubuntu are they started by inet xinet sane what?
[email]dhorner@usa.net[/email]
Where can i get real manuals for ubuntu and samba

---

### Post by Gimpy_Rob on 2007-06-17
> **langi280179 said:**
> 

```

sudo /etc/init.d/samba restart

```


That IS how you restart SMB (windows share)

Replace "restart" with start and stop to do those actions.

Now, smb is really complex, and beyond the scope of these questions.  Setting the security to share is usually a pretty good way to "just make it work"

The full manual for SMB is found by typing ```
man smb.conf
```

6800 lines, quite a read.

Google is your friend for this one.

I'll post my conf file from my ubuntu server in a few, for reference.  I'll try my best to comment it as welll.

---

### Post by phonixor on 2007-06-17
on your windows pc:
disable firewalls or make sure SMB is allowed from least your Ubuntu computer...
note: some antivirus programs also install an annoying firewall... (norton for instance....)

---

### Post by dolphin_oracle on 2007-06-17
to share with the "security=user" you will need to setup samba accounts and a matching system account for each samba user.  Use the "Users and Groups" tools under the administration menus to add the system accounts.  

Then add the samba accounts

$ smbpasswd -L -a username

it will then ask for a pasword.  Both the samba username and the password must match a system account.

the samba account username and passwords are what you are being prompted for.

---

### Post by fuzzybunny on 2007-06-21
> **langi280179 said:**
> Easy way is to set 

security = share

in /etc/samba/smb.conf

and restart

That lets me into the shares on the samba computer, but if I try to go into a shared folder, it asks for a password as guest...

What am I missing here?

---

### Post by StGeorge on 2007-06-21
See this:
[http://ubuntuforums.org/showthread.php?t=244620](http://ubuntuforums.org/showthread.php?t=244620)

---

### Post by StGeorge on 2007-06-21
Re: Networked Samba with Win98SE but have no password
Finally got there and got rid of the whole Ubuntu system showing up in shared.
Won't go into my mistake as it will only confuse the issue.


OK so here goes.
How to network Ubuntu with 98 SE.

You must Network 98SE first.

1. Install Samba.

Application/Accessories/Terminal.
Wait for Terminal to load.
In terminal Type:

sudo apt-get install samba

Wait for installation to complete.

(Can be done with Synaptic Package Manager).

2. Create User.

System/Adminstration/Users and Groups.
Add User.

Account Tab:
In Username type the name by which your 98SE computer is known on the MS Network.
You must type a password and confirm. Use as Password the name given by you for the Ubuntu computer on Ubuntu install.

Advanced Tab:
In Shell Box type:
/bin/false
In Home Directory Box type:
/dev/null

User Privelages Tab:
Uncheck all boxes.

OK and close window.

Users and Groups Window:

Groups Tag:

Select User you have created and click Add button.

OK and close window.

Open Terminal:

Type:

sudo smbpasswd -e (the network name you used for the User Account)
you will be prompted for your Adminstration Password.
Next you will be asked to enter a Password and re-enter Password.
Close Terminal.

Go to your Home Folder and create a New Folder, (name it shared if you like).
Right Click on Folder:

Click on Share folder:

Drop down menu select SMB.

OK and close.

Right click on Shared Folder in home and select Properties:

Choose Emblems for folder and Permissions for access to docs within Folder.


Now access your Ubuntu Shared Folder from Win 98SE after entering the password.
Check box to remember password with Windows.

I am sure that with the command line in Terminal this can be alot quicker. For me as a Windows user who was not into DOS this was my way to get there.
I will say however as time goes by I will probably do alot more with the command line in Terminal as well as other apps.

---

### Post by StGeorge on 2007-06-21
Also See this:

[http://www.mozillaquest.com/Linux02/LinNeighborhood_Network_Neighborhood_Story-01.html](http://www.mozillaquest.com/Linux02/LinNeighborhood_Network_Neighborhood_Story-01.html)

---

