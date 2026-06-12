---
title: "access Ubuntu computer from windows computer"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by tanman on 2006-11-16
I have a question on  a network I have at home. I am running Edgy. I have one computer running Ubuntu and 2 plus a laptop on windows. I have them all set up on a network through a linksys router. All the windows computer see each other fine. My Ubuntu computer sees all the windows computers and can access folders. The Ubuntu computer shows up in the work group on the windows machines, but I can not access it. When I open up the the Ubuntu in the work group it asks for a user name and password. I have tried the user and password I use to log into my Ubuntu computer, but nothing. When I installed Samba it never asked me for a password. I am just a bit lost. If anyone has any suggestions I would appreciate it. Just as a warning though I am new to this networking and am still trying to figure it all out.
Thanks

---

### Post by huygens on 2006-11-16
OK, so well done, you already went pretty far to get your network working.

However there is one step missing and needed, as password over the network are encrypted. So you will need to use the command line to do that, no worry I will try to guide you.
First of all, go to the "Application" menu (top left of your screen by default) and go under the "Accesories" sub-menu. There sit waiting for you to click it the "Termnial".
So click it and wait a couple of second, you will see what we call the command line.
Now as I don't know your username on your linux box, I will assume it is tanman. You need to write in the Terminal the following command. To execute it, simply press the "Enter" key of your keyboard.
```
sudo smbpasswd -a tanman
```
First you will see a message ("Password:") asking you for your password. This is to get administrative rights, so enter your normal user password.
Then a second message will ask you for the network password you would like to set for tanman ("New SMB password:"), type the password you wish.
Finally, it asks you to retype it for confirmation ("Retype new SMB password:").

You're done :-) now you can try to connect from your Windows computers.

Huygens

PS: sorry if you already new about the command line, it might have then be a bit boring...

---

### Post by tanman on 2006-11-16
Thank you so much for the help. It works great. I can even access it from my XBOX360 now.
Once again thank you and I hope I can help other people once I know more about the OS

---

### Post by huygens on 2006-11-17
I am happy it helped you :-)

Good luck for the future!

Huygens

---

### Post by edgarembrace on 2006-11-19
huygens! thank you very much for this!

i've been searching around for this username/password thing when i am trying to access my linux machines and haven't found any until i stumble upon yours..

thank you very much!

have a good one

---

### Post by ZeusABJ on 2006-11-19
I also want to say "Thank You" because I was having this exact same problem and it was driving me NUTS trying to fix it!!! Now I'm sharing files between Windows and Linux like a PRO!!!

\\:D/ 

THANKS & GOD BLESS!

---

### Post by Bob_Mendon on 2006-11-19
When I tried the same thing, this happened:


bobw@bobw-desktop:~$ sudo smbpasswd -a bobw
Password:
New SMB password:
Retype new SMB password:
Unable to open/create TDB passwd
Unable to open/create TDB passwd
pdb_getsampwnam: TDB passwd (/var/lib/samba/passdb.tdb) did not exist. File successfully created.
Segmentation fault (core dumped)
bobw@bobw-desktop:~$ 


Is this a bad thing???

---

### Post by huygens on 2006-11-19
> **Bob_Mendon said:**
> Is this a bad thing???

"Bad" I don't know ;-) but not the expected or not wished behaviour that's for sure! :confused:

Could you tell us more about which version of Ubuntu you are using (I mean the version number like 6.06, or the code name like Breezy Badger, Dapper Drake or Edgy Eft).
:-k Also perhaps could you update samba (if one is available)? To do so, open Synaptic (menu System->Administration->Synaptic Package Manager), in the newly opened window, go in the Settings menu and select Repositories. Check that you have the updates and security updates selected for the "officially supported" (also sometimes called "main") packages.
Then go back to Synaptic and select the "Reload" button from the toolbar. Click on "Mark All Upgrades" and then "Apply".
You should hopefully have a newer Samba version installed. Try the smbpasswd again.
If you still have the problem, try to reinstall samba. In Synaptic, look for samba and samba-common. Right click on each package and select "Mark for Reinstallation" for each. Then click on the Apply button in the toolbar. Try the smbpasswd again.

And let us know. Good luck.

Huygens

---

### Post by U2X001 on 2006-11-21
Thanks!!!

---

### Post by gipsytony3 on 2008-01-07
thanx a lot huygens ... ur post helped me a lot .. i was stuck with this username/password thing until i found this thread ..

---

