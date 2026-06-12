---
title: "Unable to Display folder content"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by JayDeePlus on 2008-04-03
> i have 3 computer and a router..........i have setup router and setup 2 XP machines to file share.........that is working right..........try to do it with ubuntu machine.........it's able to see the main xp machine through network place on ubuntu machine......but when i click on the machine it gives me an error " The Folder Contents Could Not Be displayed" is there some plugin or package i need to install to be able to speak to a windows machine?

> here's my thing..........i'm not trying to share files on the ubuntu machine.........i'm trying to access the files on the XP machine from the ubuntu machine and recieving an error message "ubable to display folder content" i'm not getting error numbers or any details then that in the little window that popup. I'm able to see XP/other computer from ubuntu machine, but not able to display file contents or see anything on the other computers. but this computer/ubuntu machine is able to get online. i am actually on this ubuntu machine right now............i juss would like to display content off of other computers and i'm farely new to unix OS's..........

what is sambo..........i understand that i'm suppose install it, i have done so. But, i'm not able to find the program in any menu at the top left of a workspace. Is this a feature of another program? or, will it apply settings to The Network place when i try to access other computers on the network?........can someone plzzzzzzzz help me......lord!!!!! lol

> i have a belkin router......... i don't see anything that say port forwarding........but, there is something that say's virtual settings........and in this tab this is what it say

Quote:
Firewall > Virtual servers


This function will allow you to route external (Internet) calls for services such as a web server (port 80), FTP server (Port 21), or other applications through your Router to your internal network. More Info
So i'm guessing this is where i would add smb application in at, also it had a list of programs that the router would normally block and a option to allow programs or add a program. so i titled the program SMB for discription, added 2 lines one to TCP and one for UDP........there was not an option in the drop down for both for type........then it says private ip address...........so i guess in this field it's asking for the ip address of the ubuntu machine?...........so i change that to the ubuntu machine......

for the first line it says something about "inbound port" so i'm assuming this is where you wanted me to add port 137 and 139..........now it's 2 boxes..........so i do the left box with 137 and the right box 139?..........or should i do both 137 (because there is other probrams enable, like myspace, that has the same number in both boxes) and the second like i added do both boxes 139?..........

> ok i got off the phone with belkin tech support........... they walked me through adding those port to the router............not able to access files on XP machine.........then they toke me to set the ip address of ubuntu machine outside of the routers firewall.........did that and still not able to access files on XP machine............then they toke me to turn off the routers firewall completely...........this should enable all ports to the router..........tried to access files off of XP machine from ubuntu machine and still was not able to access................now i went to system > admin > Services .........and folder sharing service (Samba) is enabled...............so what's the deal here?.......

i can go to places > Networks, in this folder i see "window network" i double click on that and i see my XP MAchine..........i double click on my XP machine and it thinks for a second.........then come back with "unable to display folder content"...........

Can someone help?..........

---

### Post by Eiríkr on 2008-04-03
Within Nautilus (your file browser), try clicking the location bar (hit Ctrl+L or click View -> Location Bar if it's hidden), and type:
```
smb://IP.ADD.RE.SS
```
Replace the caps with the IP address of the Windows machine you're trying to access.  

Cheers,

Eiríkr

---

### Post by JayDeePlus on 2008-04-03
ub-freaking beleiveable................that work..............holly shyt that work!................god..........you don't even know how long i've been trying to do this and u had the answer in 2.2 second or something......lol.........this guy is a freakin geniuos or something..............lol

THNXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX!!!!!!!!!!!!!!!!!!!!!!!!!11

---

### Post by Iowan on 2008-04-03
Is Windows Firewall enabled? Is it set to allow file sharing?

---

### Post by Eiríkr on 2008-04-03
Nope, no genius, or I'd be a much richer man.  ;)  

But seriously, I've read elsewhere that there's a bug in Win XP's SMB hostname resolution functionality, such that a network of Win XP shares and Ubuntu clients will never be able to find the XP machines via the GUI -- just what you described.  But if you know the IP address, you're good to go.  

Cheers,

Eiríkr

PS -- If that does it for this thread, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  Thanks!  :)

---

### Post by gratefulfrog on 2008-04-04
I have the same problem, but after I get the host vi the OP Address, I can see al the shared floders.

Then when I try to see the contents of any of them, I get the dreaded: "The folder contents could not be displayed." message.

Any ideas?
thanks,
GF
[http://gratefulfrog.net](http://gratefulfrog.net)

---

### Post by Eiríkr on 2008-04-04
Did you ever get a login prompt, asking for username and password?  Another thing to check is what the access permissions are set to on the share on the Windows side.  Right-click one of the shared folders, select Sharing and Security, click the Permissions button, and see what usernames have access and what kind (read, create, etc).  Try adding "Everyone" to the permissions and see if that allows you to view the folder contents from Ubuntu -- but I'd only recommend using the "Everyone" cludge for testing.  :)

Cheers,

Eiríkr

---

