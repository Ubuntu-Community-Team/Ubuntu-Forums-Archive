---
title: "accessing ubuntu from a VM xp setup"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by mpooley on 2007-03-19
Hi
I've set up a VM running win XP pro and am trying to transfer files both ways.
I ran the network wizard in windows and my ubuntu shows up in my network neighbourhood but when i try to acces it - it asks for my user name and password. I tried using my ubuntu log on name and password but it rejects it.
what am i doing wrong please?

I have dis abled the xp firewall - installed netbios but cant think of anything else to do?

PS My windows share also shows in my ubunto machine but also refuses to open the folder - doesnt ask for any passwords though.



thankyou

Mike

---

### Post by alamba on 2007-03-19
Did you install samba on the ubuntu machine to share a folder? Also, how have you mapped the windows share on the ubuntu box? What error does it give?

A

---

### Post by thelinuxguy on 2007-03-19
> **mpooley said:**
> but when i try to acces it - it asks for my user name and password. I tried using my ubuntu log on name and password but it rejects it.
what am i doing wrong please?

I have dis abled the xp firewall - installed netbios but cant think of anything else to do?

PS My windows share also shows in my ubunto machine but also refuses to open the folder - doesnt ask for any passwords though.


I assume you are talking about Samba file sharing. Did you add Samba users? Samba users are not the same as your Ubuntu system users. You need to add them explicitly or import your existing system users as Samba users. Install GSambaD from the repos.  It will help you do this using a GUI.

BTW, this thread looks similar to yours: [http://ubuntuforums.org/showthread.php?t=386610](http://ubuntuforums.org/showthread.php?t=386610)

---

### Post by mpooley on 2007-03-19
h\i and thanks
i've been mucking about with this all day and all i have managed to do is make it worse (i cant see my ubuntu machine in the window network now)

I dont understand any of it really and the gsambad front end assumes  you know what you are doing. so its not been much help.

i've read the how too - and done everything i could do but to be honest i'm just groping about in the dark!


:confused:

---

### Post by thelinuxguy on 2007-03-20
> **mpooley said:**
> h\i and thanks
i've been mucking about with this all day and all i have managed to do is make it worse (i cant see my ubuntu machine in the window network now)


I would suggest you start fresh. Revert any changes you had made. So that your Ubuntu machine is visible on the network again. And then follow this guide step by step: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

Thats assuming you are on edgy. There is a similar guide for other versions.

---

### Post by mpooley on 2007-03-20
HI
I found out something very odd whilst trying to undo my changes.
I re-instated my smb.conf -- made no difference
i uninstalled and re-installed samba --  made no difference
Uninstalled gsambad and immedietly i can see my obuntu from windows again!!!

does this give a clue ?

anyway at the moment i still cant access obunto as its rejecting my user name oer passward but i think i have leaerned enough to have another goi at that

.mike

---

### Post by mpooley on 2007-03-20
Hi again - I have it working now thanks to your help . so i can log into my ubuntu  from win XP now but when i try to log into windows from ubuntu i am still getting this "The folder contents could not be displayed."
I have turned off the firewall in xp and made a shared folder is there anything else i am missing?

thans again
Mike

---

### Post by thelinuxguy on 2007-03-20
> **mpooley said:**
> 
Uninstalled gsambad and immedietly i can see my obuntu from windows again!!!


gsambad has a service start/stop option which starts/stops the samba service. Maybe the service was stopped (or gsambad stopped it when it started) and you did not start it again from gsambad. Anyways, since you are not using it this is not an issue anymore. 

About your windows share not being accessible, I did this and I can access my shares:

[INDENT]Right Click on Desktop and create a new launcher
Give it some name
Change the type to Link
URL: smb://Windows_Username@Windows_Computername_OR_IPAddress
[/INDENT]

Double click the launcher to open it. Ubuntu will ask for the domain/workgroup and the password. Enter the required values and your windows shares should be visible/accessible.

This can also be done from Places -> Network Servers.

Let me know if this works for you.

---

### Post by mpooley on 2007-03-20
Tried that but i cant change the type to link!
It gived me the option of Application - File or application in Terminal?

thanks

Mike

---

### Post by thelinuxguy on 2007-03-20
I had posted from a Dapper machine and realized that I am getting the options that you have mentioned in Edgy. 

Places -> Connect to Server is the option that we have.

[INDENT]Service type: Windows share
Server: <My windows machine IP>
Username: Windows username
Domain Name: Windows domain / workgroup
 [/INDENT]
The above gets me a link on the desktop using which I can access my windows shares. I can't access the '$' shares though and I don't have an answer for that at the moment. However the other folders that I have shared explicitly are accessible using the above.

---

