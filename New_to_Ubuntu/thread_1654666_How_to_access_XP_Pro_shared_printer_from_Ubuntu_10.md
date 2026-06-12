---
title: "How to access XP Pro shared printer from Ubuntu 10.04.1"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Mokie on 2010-12-28
I am even less than an absolute beginner, I guess.  I'm trying to get access to my printer that's on my XP Pro box.  I've set it to share just fine, but it's the Ubuntu (karmic) end that stumps me.  I've tried to follow several tutorials online, but they either talk about Windows 7 (different prompts), other versions of Ubuntu (different prompts), or they just tell you to 'follow the prompts'.  I don't even understand what the prompts are asking for.  SMB// what?  Can someone either help me or direct me to a uber-complete idiots tutorial to do this? 

Here's what I've done so far (after setting XP up for shared printing), and where I'm stuck:

System>administration>printing.  Selected "Add". Selected "+Network Printer".  Selected drop-down option "Windows Printer via SAMBA". (don't know what this means, but I think this is the correct option to select). BTW, I did sudo apt-get install samba, if that means anything).

Here's where I get stuck as I am really not good with this sort of stuff:
Dialogue box has a blank spot to type in some information for SMB Printer (or browse). It has a pre-entered prefix of smb:// which looks like it needs an IP address there? Would that be my other computer, ie 192.168.1.101?? But wait, underneath it says, as an example, smb://[workgroup/]server[port]/printer.  I'm confused as to what to enter in this box. (again, I guess I'm less than an absolute beginner, as it appears that even an AB should know all this).

Below that it has Authentication.  Radio button for either "Prompt user if authentication is required" or "Set authentication details now".  I don't want the other computer user to have to know my Windows log-in password, if that's what it's asking for.  I just want them to click "Print" and it will simply print to the printer.  Is that possible?  If I try to 'set authentication now' it asks for my Windows password, says it's not a valid password, then just hangs up if I try it again. 

I wish there was a good tutorial for this for someone who doesn't even understand the prompts.  I've looked, but have been unable to find anything and I wasn't able to find anything in your forums that help.  I sure would appreciate any assistance, thanks!

---

### Post by davidmohammed on 2010-12-28
google brought [this]("http://www.watchingthenet.com/connecting-to-shared-printers-on-windows-computers.html") search result - hope it helps.

---

### Post by Mokie on 2010-12-28
Thank you David, but this is one of those tutorials that confused me.  Again, I don't get the same prompts at all. I get a dialogue box that asks me to enter information about an SMB Printer.  Seriously, I don't know what to enter here.  I have gone through about 18 tutorials so far.  Each one left me where I started.  I can't find one that matches what I get when I start the system>applications>printer process.  I'm still stumped.

---

### Post by withnail420 on 2010-12-28
It's probably going to be easier to run the printer from the linux box and share it to the windows one. Perhaps.

---

### Post by Morbius1 on 2010-12-28
> Here's where I get stuck as I am really not good with this sort of stuff:
Dialogue box has a blank spot to type in some information for SMB  Printer (or browse). If the samba gods are smiling upon you today you should have been able to click on the "Browse" button and it should have displayed the printers available.

> It has a pre-entered prefix of smb:// which looks  like it needs an IP address there? Would that be my other computer, ie  192.168.1.101?? But wait, underneath it says, as an example,  smb://[workgroup/]server[:razz:ort]/printer.   I'm confused as to what to enter in this box. (again, I guess I'm less  than an absolute beginner, as it appears that even an AB should know  all this).It doesn't have to be a ip address it could be any of these formats:
> WORKGROUP_NAME/MACHINE_NAME/WinPrinter
MACHINE_NAME/WinPrinter
192.168.0.100/WinPrinter> Below that it has Authentication.  Radio button for either "Prompt user  if authentication is required" or "Set authentication details now".  I  don't want the other computer user to have to know my Windows log-in  password, if that's what it's asking for.Leave it at "Prompt....".

---

### Post by garvinrick4 on 2010-12-28
I agree with just setting the windows xp machine up in a workgroup and your ubuntu will
see the workgroup out of box. It is just setting up the windows machine Ubuntu is ready to go.
This is the add printer in ubuntu

---

### Post by Mokie on 2010-12-28
WithNail, I had set the printer up in ubuntu (major ordeal), but I mainly use the XP box, so I switched it over and deleted the printer from Ubuntu.  Don't wanna go through that again.  Garvinrick, not sure what you mean.
Morbius1, questions!  I clicked on browse, left it on prompt.  I got an authentication box asking for my user name and password. I entered my Windows login name and pass, but it failed.  I called the place I purchased the computer, and he said there might be another password set somewhere (?) and since he didn't know windows, he couldn't help me.  So, I can't progress any further until I know what user name and pass it's wanting me to enter.  Also, does this mean I will have to give the user of my Ubuntu machine my windows log-in name and password so they can print?  Ugh, that's terrible if so.

---

### Post by Morbius1 on 2010-12-28
When you shared the printer on WinXP you should have seen a box that looks like this. To be honest I don't remember if there's even a way to make WinXP prompt for a username and password. Are you sure you shared the printer on WinXP?

---

### Post by Mokie on 2010-12-28
So, I entered HOMEOFFICE/ASUS/hpC5240, ignored the authentication box and clicked "forward".

It asked me to choose a driver, then the model number. Then I selected 'Print test page'.  Came back with error: "Idle - tree connect failed (NT_STATUS_ACCESS_DENIED).  Up pops the authentication box asking for user name and password. It keeps pre-filling in my user name to log into Ubuntu, don't know why.  Should I be using the Ubuntu log/pass or my Windows log/pass? When I use the Ubuntu login/pass, it just give me the Auth window again.  When I use my Windows login/pass, I get the "tree connect failed" error message again.  Now what?  (And thanks for all your help so far).....

And, Morbius, yes I did enable sharing.  The shared printer shows up when I click on 'browse' in Ubuntu.  Just can't make anything else happen.  I even went back and did it again just to see if I had to set some kind of password... nope.

[IMG]http://i971.photobucket.com/albums/ae195/CommunityAccount/Screenshot-1.png[/IMG]

---

### Post by garvinrick4 on 2010-12-28
You have to have a login user and password set in Windows before Workgroup will function. And have to be set to login not login automatically.

---

### Post by Mokie on 2010-12-28
If I'm understanding what you're saying, I already have a user name and password set up.  You cannot use my Windows box without it.  It's not set up to log you in automatically. I'm kinda confused as to what you mean?

I found a page where a couple of other people had this problem.  They eventually put this into the smb:// text box:


smb://usrername: password@server/printer  (I (put a blank after : to avoid a smiley being displayed))

I tried this: 

smb://username: password@192.168.1.101/HP_C5240

and this:

smb://username:  password@ASUS/HP_C5240

Both still gave me the error.  BTW, while I was sitting here, little box came up that said something like "Job printing to HP_C5240".  Nothing has printed yet, however. Here's what my queue looks like now:

(Apparently these are all trying to print, some needed authentication but now show as pending.  Not sure about the one that's being 'held' - it's past the time and nothing has printed.)

[IMG]http://i971.photobucket.com/albums/ae195/CommunityAccount/Screenshot-2.png[/IMG]

---

### Post by Mokie on 2010-12-28
To continue the saga:  As I was perusing through more google search results, these all popped up.  I tried using my windows login name and pass, and my ubuntu user login name and pass.  Even tried them with u/c and l/c, all caps, all lowercase, every combo I could think of.  Nothing works.  I'm really at a loss, as the printer seems to WANT to print, but for some reason, authentication is failing.  Is there maybe something wrong with CUPS (I'm not knowledgeable in that area) or something in my router, or ????  Is what I'm trying to do really just not a capability of Ubuntu?

[IMG]http://i971.photobucket.com/albums/ae195/CommunityAccount/Screenshot-3-1.png[/IMG]

---

### Post by Mokie on 2010-12-28
I just hooked my printer up directly to my Ubuntu machine and it printed  a test page just fine.  I might attempt to set it up as my sharing machine,  but this is definitely not my ideal solution.  It seems that I should be able to share from my  Windows machine just as easily, so I would still really appreciate any  suggestions as to how to fix this problem.  I've included a few links  that I found that might be 'helpful' (Seems like this forum has seen this problem before with no luck solving) . I'm not expert enough to  extrapolate a solution, but if you are, I would really like to do this  the way I originally intended to.  So, I'm still looking for help!

[http://ubuntuforums.org/showthread.php?t=1128323](http://ubuntuforums.org/showthread.php?t=1128323)
[http://forums.gentoo.org/viewtopic-t-501756-start-0.html](http://forums.gentoo.org/viewtopic-t-501756-start-0.html)
[http://www.linuxquestions.org/questions/linux-newbie-8/printing-through-samba-and-cups-cant-connect-to-host-226289/](http://www.linuxquestions.org/questions/linux-newbie-8/printing-through-samba-and-cups-cant-connect-to-host-226289/)
[http://ubuntuforums.org/showthread.php?t=492306](http://ubuntuforums.org/showthread.php?t=492306)

---

### Post by Jerry N on 2010-12-28
I can't troubleshoot your specific problem but it sounds like things have gotten much too complicated.  I try a lot of Linux distributions so I set up a printer from a Windows server quite often - usually a server running Win2000 (I tried a Linux server but found it far easier to use Win2000).  I have an HP 7960 connected directly to my Win 7 primary computer.  From Ubuntu 10.04, I went through "System", "Administration", and "Printing".  There I got a list of printers already installed.  I told it to "ADD" a printer and then "Windows Printer Via Samba".  Selecting "Browse" should show all computers in the workgroup and selecting the correct workgroup computer should give a list of printers that are set up for sharing on that computer.  This can take a few minutes and when it searches for drivers it won't find any.  You then go through the list presented and select the correct printer.  The driver installs and away you go!

It always works this way for me.

Jerry

---

### Post by Mokie on 2010-12-29
Jerry, thanks for your response.  I have done exactly what you did, that is how I got to where I am.  Where I seem to be getting hung up is with authentication.  When I select 'browse' I get the list of computers.  My Windows box is there, but when I click on it, I am asked to authenticate with a username and password.  No matter what I use, (My Windows logon, my Ubuntu logon, I've even tried Guest with no password), it fails. If I skip the 'browse" and enter the path, then it seems to send a test page to the print queue, but then up pops an authentication box again.  Of course, since none of my user names/passwords work, it also fails. Then the print job languishes in the queue due to no authentication.  I need help figuring out why Ubuntu won't accept my user name and password.

---

### Post by garvinrick4 on 2010-12-29
It is in the set-up in your windows box for your workgroup.

---

### Post by Mokie on 2010-12-29
Garvinrick4:  Could you please explain what 'it' is? What do I need to do in the Windows system?  I am new at all this so I really need more detail, thank you!

---

### Post by garvinrick4 on 2010-12-29
Are you new to Windows and Linux?
#I can remember setting up Windows systems for workgroup and you have to share anything you want to be shared such as printers, media, documents whatever has to
be shared, I believe it was a right click and check share. 
 Had to use your login and password to get into system or workgroup does not function.
#It uses that login and password to access shares. 
#System Properties had computer name and workgroup settings.
#There was a network and sharing center to turn on media sharing, printer sharing and so on.
#I am sure there is a help document in Windows also.
# But I do know Ubuntu is set up to work out of box if windows workgroup is set up right in Windows, that is where you should concentrate.

---

### Post by Jerry N on 2010-12-29
> **garvinrick4 said:**
>  
.... Had to use your login and password to get into system or workgroup does not function.
#It uses that login and password to access shares. 
#System Properties had computer name and workgroup settings.


??  I never use a login and password to get into my Windows systems (Win2000, Win XP, Win 7) and I can share files and printers just fine.  There is an extra step or two in Win 7 to set up sharing in the first place because you have to tell it who to share with (everyone).  

Jerry

---

### Post by Morbius1 on 2010-12-29
And what happens when you change this:
>  smb://username: password@192.168.1.101/HP_C5240to this:
> smb://[COLOR=Blue]guest[/COLOR]@192.168.1.101/HP_C5240OR this:
> smb://[COLOR=Blue]guest[/COLOR]@ASUS/HP_C5240

---

### Post by Mokie on 2010-12-29
Thank you Jerry.  Morbius1, I did try those combinations, and also with Guest capitalized, because that's how it shows up in my users screen.  I had found a thread that mentioned enabling the Guest account, although I already had Guest enabled. Still, with each combination, each time I try to print a test page, Ubuntu responds with the Authentication dialogue box.  I tried Guest and guest with no password as well, but still I get the response "Tree connect failed - (NT_STATUS_ACCESS_DENIED)"  The test page sits in the queue and occasionally up pops the Authentication box asking for user and password, until I delete the file from the queue.  I'm looking into CUPS, (foreign territory for me) but maybe there is some setting that I'm missing on my Windows box somewhere.  I've followed all the stops to enable printer sharing, and have repeated them a couple of times, so I really don't know what else could be the problem. I'm sure it's something super simple and obvious.  Just wish it would pop out and hit me sooner rather than later.

---

### Post by Morbius1 on 2010-12-29
why not post your printers.conf file:

```
cat /etc/cups/printers.conf
```

---

### Post by Mokie on 2010-12-29
Morbius1, this is what printed on screen when I typed that cat line you suggested:

# Printer Configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING

I'm not sure what this means?

PS I did an apt-get install for CUPS and for SAMBA, both said I already have the newest version.

Morbius1, I just thought of something... (see the other thread I posted about installing WOW).  I installed a firewall - Firestarter, I think, and opened some ports for WOW.  I saw somewhere that printing typically occurs on port 631. (Bear with me, this is still new territory for me, ports and all).  Would my firewall be causing the problem?  I would just as soon delete everything I did associated with WOW on my Ubuntu box, should I close those ports and remove the firewall? Or leave it and open 631 if it isn't?

---

### Post by Morbius1 on 2010-12-29
Sorry, had a senior moment there:
```
sudo cat /etc/cups/printers.conf
```As far as port 631, it's true that cups runs on port 631 on Linux. You're accessing the printer via samba though so I'm not sure how all that plays out. When in doubt open the port: 631/tcp and 631/udp.

As far a firestarter is concerned I don't think much of it. In fact there are some Samba HowTo's that go as far as stating that if you have it installed uninstall it. I don't use firewalls on my systems ( except Windows of course ) since I'm behind a router and most of my systems are desktops so I don't have first hand knowledge of Firestarter.

You might , at least temporarily, disable firewalls on both Linux and Windows and see if things clear up.

---

### Post by Jerry N on 2010-12-29
> **Morbius1 said:**
> 
You might , at least temporarily, disable firewalls on both Linux and Windows and see if things clear up.

You reminded me of something - I use Zonealarm on my Windows machines and on a computer with Zonealarm it is necessary to specify what other IP addresses on the LAN are allowed to access that computer.  I generally set it to the full range of IP addresses that the router might assign.  I don't use any other Windows firewalls so I don't know if other firewalls need the allowable IP addresses set or not.

Jerry

---

### Post by Mokie on 2010-12-29
Morbius1 and Jerry.... I really appreciate you two hanging in there with me.  Morb, I did use sudo (that much I know to do!) and that's what printed.  Jerry, I also use ZoneAlarm, so I checked my trusted zone, apparently Windows automatically sets the ranges, but I went ahead and added my Ubuntu box IP all by itself just to be sure. Still getting the same error.  Then I tried using the 'help' tab after going into system>administration>printing, and there was a 'troubleshooting option'. It had me go into server settings and check the box that says "Publish shared printers connected to this system",  Then it asked if I wanted to enable debugging, so I did. Then it asked if I wanted to print a test page (I was getting excited by this time, lol), so I said, why, sure!  Then it just hung up. Ugh. I clicked cancel and it opened up the 'Printing trougbleshooter Error log messages' box, with a bunch of cups code in it that I don't understand.  So that's where I am at this point. Oh, just now (29 minutes after starting the test print) a little box came up and said Printing started on Hp-Photosmart-C5200.  I opened the Print Queue and it's there (again) but it's 'processing.'   I'm really stumped.

Seems this problem has been around for awhile... what do you think of the solution(s) offered?  Would it work in my situation?  [http://ubuntuforums.org/showthread.php?t=1249318](http://ubuntuforums.org/showthread.php?t=1249318)

---

### Post by Morbius1 on 2010-12-30
>  Morb, I did use sudo (that much I know to do!) and that's what printed.  If this is all you got from /etc/cups/printers.conf:
> # Printer Configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING then you do indeed have a problem. My first thought is that you don't have cups running so see if it's started:
```
sudo service cups status
```If it's not started then start it:
```
sudo service cups start
```And for good measure restart samba:
```
sudo service smbd restart
```Wait about 5 minutes ( I'm not kidding ) and then remove the current Windows printer and add it back again in the Ubuntu printer utility.

Then pray [-o<

---

### Post by nebileix on 2010-12-30
Maybe u share a folder in windows first and see whether can u access that folder in ubuntu to narrow the issue to printer only rather then samba share.

---

