---
title: "sharing printer to windows clients"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by dbrum on 2006-09-29
I have a HP printer on my Ubuntu works fine locally.  I shared it and my user home directory with samba.

From my windows box, I can see my ubuntu machine in the same workgroup no problems.  Problem is, when I try and access the Ubuntu from win, it asks me for a user/pw, which I typed in the user combo, the root, tried everything.  Can't "log in".  What have I done wrong?  What login information is it authenticating against and how do I set it properly?

thanks.

---

### Post by mitch.c on 2006-09-29
> **dbrum said:**
> I have a HP printer on my Ubuntu works fine locally.  I shared it and my user home directory with samba.

From my windows box, I can see my ubuntu machine in the same workgroup no problems.  Problem is, when I try and access the Ubuntu from win, it asks me for a user/pw, which I typed in the user combo, the root, tried everything.  Can't "log in".  What have I done wrong?  What login information is it authenticating against and how do I set it properly?

thanks.

Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(**Dapper**: /etc/cups/cups.d/ports.conf; **Edgy**: /etc/cups/cupsd.conf)
```
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
```

Restart the cups daemon:
```
sudo /etc/init.d/cupsys restart
```

On the Windows box:
[LIST=1]
[*]Start the **Add Printer** wizard
[*]Click **Next**
[*]Select **A network printer, or a printer attached to another computer**
[*]Select **Connect to a printer on the Internet or on a home or office network**
[*]Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the **URL** box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. **Don't forget the port number!**
[*]Click **Next** and run through the driver installation to complete
[/LIST]

Should work just fine.

---

### Post by dbrum on 2006-09-29
Hi Mitch.  thanks for the help.

Now I remember going into the CUPS web admin console, and not being able to log in.  I just tried it now, and as soon as I try and commit a change, it asks me for a user name and p.w.  i tried my own user I am logged in with which has admin rights and it did not work.  I tried root, and same thing... can't make any changes to the cups system with the web gui console tool.

I will try your suggestions now thanks.  If you have any ideas why I would not be able to make changes with the cups console, please let me know.  I searched posts here and others have had the same issue, but I could not find a solution.

thanks.

---

### Post by mitch.c on 2006-09-29
> **dbrum said:**
> I just tried it now, and as soon as I try and commit a change, it asks me for a user name and p.w.  i tried my own user I am logged in with which has admin rights and it did not work.  I tried root, and same thing... can't make any changes to the cups system with the web gui console tool.

I will try your suggestions now thanks.  If you have any ideas why I would not be able to make changes with the cups console, please let me know.  I searched posts here and others have had the same issue, but I could not find a solution.

thanks.
You can't use the web admin interface because root is disabled. If you want to configure cups so that you can use web admin w/o enabling the root account follow the instructions here: [https://help.ubuntu.com/community/PrintingCupsWebInterface](https://help.ubuntu.com/community/PrintingCupsWebInterface)

---

### Post by dbrum on 2006-09-30
Your first suggestion got my share working with my windows box.

thanks.

---

### Post by niki001 on 2006-10-19
Mitch.c You wrote the following:

Save yourself some headaches (assuming this is a private network):
 
Code:
#/etc/cups/cups.d/ports.conf
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock

Can you tell me what exactly I must do with that code. I'm a full newbie on Linux and I'm having a simular problem. I already know some things about the console but for the moment I havent got a clue :confused: about the code...

Thx for the advice

---

### Post by mitch.c on 2006-10-19
> **niki001 said:**
> Mitch.c You wrote the following:

Save yourself some headaches (assuming this is a private network):
 
Code:
#/etc/cups/cups.d/ports.conf
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock

Can you tell me what exactly I must do with that code. I'm a full newbie on Linux and I'm having a simular problem. I already know some things about the console but for the moment I havent got a clue :confused: about the code...

Thx for the advice
Put the last two lines (the first two are comments) in /etc/cups/cups.d/ports.conf

---

### Post by kpictjl on 2006-10-22
> **mitch.c said:**
> 
Restart the cups daemon:
```
sudo /etc/init.d/cups restart
```

Typo in the above, missed the "sys"
```
sudo /etc/init.d/cupsys restart
```

The procedure worked great...but I have no idea what it did.  What's the 631?  Is it basically opening a software socket between the 2 machines or something?  So would this work for multiple machines on the same network all using the same #631.

---

### Post by mitch.c on 2006-10-23
> **kpictjl said:**
> Typo in the above, missed the "sys"
```
sudo /etc/init.d/cupsys restart
```

The procedure worked great...but I have no idea what it did.  What's the 631?  Is it basically opening a software socket between the 2 machines or something?  So would this work for multiple machines on the same network all using the same #631.
Your just telling the cupsd to accept any connection on port 631. The default only allows connections for the local host. You could change it to only accept connections from specific subnets if desired.

BTW, thanks for pointing out the typo... fixed it in the original post.

---

### Post by kpictjl on 2006-10-23
Before I changed ports.conf from "#Listen localhost:631" to "Listen *:631" I was able to print intermittently from my windows machine and it took several minutes to open the printer's property dialoge on the windows machine.  Something was causing big time latency.

Assuming localhost means "my ubuntu machine" then why did printing from my windows machine work before at all?

---

### Post by beast2k on 2006-10-26
I'm using Ubuntu 6.10 with a HP Laserjet 1018 with no firewalls on a network with 2 XP machines and well it's the same old ubuntu print share problem, I tried all the usual fixes and hacks and nothing, does/will anyone have a fix for this problem ? there seems to be some sort of ongoing trouble with print sharing and ubuntu, the posts on this topic date back quite a ways and they were all helpful in their time however I need a fix for 6.10. Any ideas ?

---

### Post by kpictjl on 2006-10-28
I updated to edgy, 6.10, and now remote printing from my windows xp machine does not work. Printers and Faxes in XP says "operation cannot be completed." I walked through this procedure again, Some things, like the *:631 had been reverted back to localhost:631.  Is there something new about edgy that need to do?  I can print locally, but not remotely.

Thanks,

---

### Post by beast2k on 2006-10-29
I was having the exact same problem I have to use Mandriva 2006 to print share (with 2 kids in high school they need a priner badly). My HP1018 works perfect in mandriva2006 and shares perfect as well, my next question is can I simply copy the cups directory and all the printer related files to ubuntu to make it work? Linux is linux right? sort of ? or is the problem more deeply rooted than simply cups and it's related files? any thoughts or ideas on this? anyone?

---

### Post by patrick295767 on 2006-11-11
> **dbrum said:**
> Hi Mitch.  thanks for the help.

Now I remember going into the CUPS web admin console, and not being able to log in.  I just tried it now, and as soon as I try and commit a change, it asks me for a user name and p.w.  i tried my own user I am logged in with which has admin rights and it did not work.  I tried root, and same thing... can't make any changes to the cups system with the web gui console tool.

I will try your suggestions now thanks.  If you have any ideas why I would not be able to make changes with the cups console, please let me know.  I searched posts here and others have had the same issue, but I could not find a solution.

thanks.
I guess typing  : 
```
sudo smbpasswd -a username 
```
 will help for your samba problem above
  (/etc/cups/cups.d/ports.conf is important)

---

### Post by Sytone on 2006-11-22
As a FYI I found the config on the following path:

/etc/cups/cupsd.conf

---

### Post by bruceathome on 2006-12-17
Thanks mitch.c, worked an absolute treat.  Greatly impressed the wife setting up print sharing!


Fiddled around for days trying to get print sharing through samba to work, and then found this thread.  Really appreciate your efforts in helping the community.

---

### Post by kpictjl on 2006-12-17
> **bruceathome said:**
> Greatly impressed the wife setting up print sharing!


You are a lucky man.  My wife was not impressed at all.  She was like, yeah you and every other printer in the world.  I guess I'm happy to impress myself:)

---

### Post by wh0rd on 2006-12-19
Thanks a lot. It worked really well.

---

### Post by MeduZa on 2006-12-26
I follow this great how-to to share my printer on my local network and works, but I put an extra feature, if you like to share your printer on your local network only, I used: [COLOR="Blue"]Listen 192.168*:631[/COLOR] instead of [COLOR="Blue"]*:631[/COLOR] 
If that working in the way I need or is a stupid idea?
The idea is to share only to IPs starting with 192.168 that means local network
right?

---

### Post by taylonr on 2006-12-27
I tried changing the listener in the file and went to my XP box to install the printer.
I entered my information ([http://desktop_server:631/printers/psc1315](http://desktop_server:631/printers/psc1315)) and clicked to the next screen.  I was prompted to print anonymously, log in or use the windows domain login.  I tried anonymously and was told it was not allowed, I then tried loggin in as both 'root' and 'nate' and was not allowed.  The message is "you do not have access to the printer, please try a different username or password"

Any ideas?

---

### Post by mitch.c on 2006-12-27
> **taylonr said:**
> I tried changing the listener in the file and went to my XP box to install the printer.
Not sure what you mean by 'listener'... maybe you could be more specific.
> **taylonr said:**
> I entered my information ([http://desktop_server:631/printers/psc1315](http://desktop_server:631/printers/psc1315)) and clicked to the next screen.  I was prompted to print anonymously, log in or use the windows domain login.  I tried anonymously and was told it was not allowed, I then tried loggin in as both 'root' and 'nate' and was not allowed.  The message is "you do not have access to the printer, please try a different username or password"

Any ideas?

Make sure you have something like this in /etc/cups/cupsd.conf
```
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>
```
You might also try this command at a shell prompt (just to make sure your printer is accepting jobs from all users):
```
$ sudo lpadmin -p psc1315 -E -u allow:all
```
If this doesn't help, you might post your cupsd.conf, and if on Dapper, /etc/cups/cups.d/ports.conf, /etc/cups/cups.d/browse.conf

---

### Post by taylonr on 2006-12-27
Wow, thanks for the quick response.  I actually was coming in here to say that I resolved that part. 

However, now when I click next after entering the address it prompts me for a driver.  However, XP does not have my printer (PSC 1310) in the driver list.  I pulled out my CD from HP and ran the installation, tried connecting again through :631 etc and it still prompts for my driver.  

This appears to be an hp thing, since other people haven't had any problems finding drivers in windows. 

Thanks

---

### Post by mitch.c on 2006-12-27
> **taylonr said:**
> when I click next after entering the address it prompts me for a driver.  However, XP does not have my printer (PSC 1310) in the driver list.  I pulled out my CD from HP and ran the installation, tried connecting again through :631 etc and it still prompts for my driver. 
That's normal. You still need to install the Win XP driver, and select it from the Manufacturer -> HP (or Hewlett Packard) section. If it doesn't appear, then it's not yet installed.

HP driver "installers" often do nothing more then unzip the driver files and place them in a folder on the C: drive. I just ran one of these today for an HP LJ 3015... the files needed to actually install the driver were deposited in C:\lj30xx-3080\.

If this is the case, then when XP prompts for the driver, select Have Disk, and browse to the folder that contains the files.

---

### Post by taylonr on 2006-12-27
Thanks again for your help.  I'm still having a problem though.

On the XP machine, I uninstalled the printer and all its software.
Then I took my HP CD, put it in and ran through the entire install process (including connecting the printer to a USB port.)  It installed fine.

However, when I was asked for a driver doing the ipp way, it was still not in the windows list.  I went through every INF file that was on the CD and windows repeatedly told me that file did not contain information about my printer.  

I looked around on the HDD and found a drivers folder in Program Files/HP, but none of those files were inf and that is what windows is wanting. 

I tried ipp because I couldn't get cupsaddsmb to create a driver to export to the windows computer.

I googled a bit and found some people saying that an HP PSC 1315 only works on a windows-to-windows network, i'm not sure if it's true or not.

Any suggestions?

---

### Post by fredds on 2006-12-28
When it says browse CD, click ENU, drivers, WIN2K_XP.
Worked for me.
If you are setting up as a network printer, you shouldn't need to connect the printer to the windows machine during installation, only the Linux machine.

cheers

Fredd

---

### Post by taylonr on 2006-12-28
Thanks Fredd, unfortunately, my CD doesn't have a W2k folder there.  I don't want to thread jack this thread away from ipp so I've started a new thread about my particular printer and its problem.

[Here's the new thread](http://ubuntuforums.org/showthread.php?t=326824)

---

### Post by pksings on 2007-02-01
One more thing that I had to do. Apparently my windows machine was trying to print as the user 'samba'.   So I had to add in /etc/cups/printer.conf 

"AllowUser samba"

Along with all the other user names. Until I did that I was getting an over quota message and it wouldn't print.


PK

---

### Post by pksings on 2007-02-01
Edit /etc/cups/printers.conf

Add the following without the quotes. I put it with all the other user allow lines.

"AllowUser samba"

restart cupsys, /etc/init.d/cupsys restart.


Works like a champ.

---

### Post by porschevic on 2007-02-15
> **taylonr said:**
> I tried changing the listener in the file and went to my XP box to install the printer.
I entered my information ([http://desktop_server:631/printers/psc1315](http://desktop_server:631/printers/psc1315)) and clicked to the next screen.  I was prompted to print anonymously, log in or use the windows domain login.  I tried anonymously and was told it was not allowed, I then tried loggin in as both 'root' and 'nate' and was not allowed.  The message is "you do not have access to the printer, please try a different username or password"

Any ideas?


Encountered the same XP error message and resolved it by creating a username on the ubuntu/printer box, and then added that user to the 'lpadmin' group.  Then, when you add the printer through XP, connect as that user.

---

### Post by The Scientist on 2007-09-22
> **mitch.c said:**
> Save yourself some headaches (assuming this is a private network), edit the Listen directives in the following file:
(**Dapper**: /etc/cups/cups.d/ports.conf; **Edgy**: /etc/cups/cupsd.conf)
```
#Listen localhost:631
Listen *:631
Listen /var/run/cups/cups.sock
```

Restart the cups daemon:
```
sudo /etc/init.d/cupsys restart
```

On the Windows box:
[LIST=1]
[*]Start the **Add Printer** wizard
[*]Click **Next**
[*]Select **A network printer, or a printer attached to another computer**
[*]Select **Connect to a printer on the Internet or on a home or office network**
[*]Type [http://server_name:631/printers/printer_name](http://server_name:631/printers/printer_name) in the **URL** box, where server_name is the hostname or ip address for the ubuntu machine, and printer_name is... the printer name. **Don't forget the port number!**
[*]Click **Next** and run through the driver installation to complete
[/LIST]

Should work just fine.

Thanks a lot. The windows PC found the printer .. That's something.
I think I've done something wrong with the drivers as it's not printing .. yet.

---

### Post by SevenNinety on 2008-01-19
I got the sharing with windows working, but the first time I try to print from windows (after my ubuntu box has been rebooted) one or two lines are printed then the paper is spit out and the printer won't print any more.  If I go to system - administration - printing and look at the policies tab, I see that the enabled check box is cleared.  Checking it again fixes the problem until I reboot my ubuntu machine.  Any ideas why this is happening?

---

### Post by geokker on 2008-01-22
192.168.3.*:631 didn't work on my Gutsy machine. *:631 works fine. Does this mean hordes of malicious hackers will try to print counterfeit $100 bills on my inkjet?

---

### Post by ockron on 2008-04-07
Hi Guys .... Nooby here.

I followed the instructions as best as I could and can somehow see the printer from my XP laptop.

I get the error "Access denied, unable to connect." 

Please help!!

---

### Post by tenisbumjc@hotmail.com on 2008-07-17
I am not sure where I need to post this.
I have a HP Officejet Pro L7780 printer that is hooked up via wireless to rest of my home/office.
I am totally new to Linux-Ubuntu. I have Ubuntu installed as a dual boot on one of my windows servers.. Windows can print fine.

I have not been able to install the printer drivers in Linux using the hplip file that I was directed to. I opened the terminal window to my user desktop and typed in the file name but the response was it could not run.
Anyone have an idea what I am doing wrong??

---

