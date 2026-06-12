---
title: "Networked Samba with Win98SE but have no password"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by StGeorge on 2006-08-26
My Laptop has been networked with Samba to a desktop with Win 98SE.
I can see my shared folders from my 98SE desktop on my Ubuntu laptop, but when I try to access my shared folder on my laptop from my desktop I get asked for a password.
I haven't set up a password so it looks like Samba has automatically created one.
I accessed and extracted smbpasswd. It does not show any password.
Any ideas how I can find this password.

---

### Post by reef2dive on 2006-08-26
I do not think the problem is on linux laptop but on the win-desktop.
To my experience, you need to have a user on your on win98 machine, as samba always will do some kind of authentication. I assume that you like most win98se users do not have a user and a pwd. Create the same user and pwd as on your linux box on the win98se machine. That works for me. And then the login will be automatic.

---

### Post by StGeorge on 2006-08-27
You assume correct.
I have no Login Password.
I have changed the password on 98SE to my Ubuntu Password but still cannot access my Ubuntu Shared folder.
I would like to change my Ubuntu Username and Password which was setup on install a few days ago, but I do not know how to do it.
I would like to have no Username and Password for Ubuntu as I can easily setup a password in BIOS.

---

### Post by JimT on 2006-08-30
I have the same problem. 
One of the reasons I dumped Win 2000 was because of this.
Is there any way to setup Samba not to use a password??

Jim

---

### Post by huygens on 2006-08-30
No your problem is that you need to set up a SMB password (encrypted one). What you need to do is type in a terminal this (on your Linux laptop):
```
sudo smbpasswd -a *username*
``` This script will probably prompt you for the “sudo” password, and then it will prompt you for the SMB password. Please, set there the password you wish to enter from Windows.

You can find a little more explanation here: [http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185](http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185)

For your other request:
Having change your Windows password to your Ubuntu one might help you after having done the above steps. As Windows will try automatically your password :-)
If you wish to change your Ubuntu password, you can do it here on a terminal:```
passwd
``` If you wish to change your login, you can do it in two ways:
[U][B]Simple
[/B][/U]```
gksudo gedit /etc/passwd
``` 
In this file at the bottom you will find something like:
```
username:x:1000:1000:your full name,,,:/home/username:/bin/bash
``` Simply change the username that is at the beginning of this line! /!\ Not the second time where it appears later on that line, so you will have something like:
```
**new_username**:x:1000:1000:your full name,,,:/home/username:/bin/bash
``` That's it!

[U][B]Less simple
[/B][/U]OK, you will have to edit the same file, but this time you need to logout before doing it. once you are log out and you have the graphical prompt asking you your username. Press the key combination: Ctrl+Alt+F1
enter here your username and password.
Then do this:
```
cd /
sudo nano /etc/passwd
``` Modify the line as suggest above, but change also the second occurence of your username, so it looks like this:
```
**new_username**:x:1000:1000:your full name,,,:/home/**new_username**:/bin/bash
``` And then save the file by pressing Ctrl+O, then exit by pressing Ctrl+X.
Type the following commands:
```
sudo mv /home/{username,new_username}
exit
``` Press Ctrl+Alt+F7, you are back to your graphical login prompt. Enter the new user name and your password :-) That's it...

Then you request to have no username and no password... Well this is not possible. At least there is a way that Gnome goes directly to your session and opens it without you entering a password. But I do not remember how to set it, and I would not recommend it.

---

### Post by StGeorge on 2006-08-31
Tried all ideas above.
Doesn't work for me.
Tried below which is for XP. Doesn't work for me.

[http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185](http://www.ubuntuforums.org/showthread.php?p=1333185#post1333185)

Problem is now that I have set up user which will require deletion.
I certainly will not play with windows network to make this work as it is the server for ICS.
Why oh why am I playing with passwords. (6 hours of time to date to sort this).
I have enabled full access to my shared folder on Ubuntu, I would have thought that was enough.
The problem as I see it is that I can't get past my networked Ubuntu laptop
from my 98SE desktop to the shared folder on my laptop.
The box I was getting was password for \\LAPTOP1\IPC$.
After trying suggestions all I get is a dialogue box \\LAPTOP1 is not accessible.
It has gone from bad to worse.
At least Windows lets me access shared folders on my desktop so I can transfer docs etc through windows.

Will give up for now as I might have to get used to limited functions with Ubuntu.
Having said all that my third install was a breeze.
Yes I had to install 3 times because I was having problems with partitioning.
Crashed Ubuntu once.
In the end I deleted all the partitions on my laptop and let Ubuntu take what it wanted during install.

Installing software was easy as I followed the advice given here:

[http://pcmech.com/show/os/917/1/](http://pcmech.com/show/os/917/1/)

A great transition guide.

---

### Post by StGeorge on 2006-08-31
An afterthought.
I have done all I can to eradicate windows passwords and users on my desktop because I have software for encryption of files and folders. Software for hiding drives. My supervisor password is set up in BIOS. My User Boot password is set up in BIOS. The only windows password I use is for Screensaver. I have a quick lauch screensaver link so when I leave my machine I push a button and thats it.

I agree with all thats been said that it is a bad idea to erradicate any supervisor passwords with Ubuntu.
As this is a personal laptop as are most laptops. Creating users in the most cases is pointless.

I haven't looked into screensaver password for Ubuntu yet as I am still configuring machine. Besides I have no valuable data on Laptop as yet as I am playing with prefered software to see what I want.
That in itself will take time as the choice is amazing.

Getting used to a new OS is time consuming but it has to be said that the amount of time fixing Windows over the past 6 years will make working with Linux worthwhile.

---

### Post by bigken on 2006-08-31
in the terminal type
sudo apt-get install samba
sudo smbpasswd -e yourname
sudo smbpasswd -a  yourname
sudo /etc/init.d/samba restart ;)

---

### Post by StGeorge on 2006-08-31
Thanks bigken.

After setting up new user and going through recomendations of XP link above and adding user to groups. (I gave the user as my desktop name on MS Network) and then followed your commands, (didn't bother with 'sudo apt-get install samba' as it was already installed), I typed in the first command you gave me, 'sudo smbpasswd -e yourname' (yourname being group username), pressed enter and voila, I entered my adminstrive password and then entered a password for the network. I went to my desktop and hey presto can see my Ubuntu shared folder.
Didn't bother with next two commands:
'sudo smbpasswd -a yourname
sudo /etc/init.d/samba restart'.
The only problem is that for some reason my desktop now has access to the whole system.
How it got into my Shared folder is beyond me.
When I open my shared folder it has nothing on the Ubuntu OS.
When I open the folder on 98SE it has program files as well as Doc Folders.
Still a little more messing about should fix that.

---

### Post by StGeorge on 2006-08-31
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
You must type a password and confirm. Use as Password the name given by you  for the Ubuntu computer on Ubuntu install.

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

### Post by StGeorge on 2006-09-11
After doing the sixth install of Ubuntu the above did not work.
The reason I keep re-installing is I have found that no Linux Distro will give me sound.
They all deaf & dumb when it comes to sound on my Laptop.

You should Set up MS Network first.

You still need to install Samba.

Still create User as above.

In Terminal Type

sudo smbpasswd -e (Your Ubuntu Login Name)
sudo smbpasswd -a (Your Ubuntu Login Name)

You will be prompted for your Adminstration Password.
Next you will be asked to enter a Password and re-enter Password.
OK and Close Terminal.


That is the password for Windows.

I also went to Administration/Networking and set up Network with Windows OS Network Name.

I've had enough of all this.

---

### Post by reaganf2 on 2007-11-23
thanks a ton hygens... was searching all over the net for a solution to access my ubuntu shares from my windows box...

---

