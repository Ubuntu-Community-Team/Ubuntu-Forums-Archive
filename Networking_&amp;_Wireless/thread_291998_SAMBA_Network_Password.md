---
title: "SAMBA Network Password"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by Steve S. on 2006-11-03
I'm trying to log in via Konqueror to see my Windows box's files from my Ubuntu box.  I can ping it fine.  I type in smb://<ip address of windows box> and it asks me for a password.  ?  The password on the windows box?  There isn't one, or it's blank.  I tried a few different password combination.  What is this?  How can I get past it/change it?

I checked out this [thread]("http://http://www.ubuntuforums.org/showthread.php?t=192281").  Is it what I'm after?  Please advise.

---

### Post by dannyboy79 on 2006-11-03
> **Steve S. said:**
> I'm trying to log in via Konqueror to see my Windows box's files from my Ubuntu box.  I can ping it fine.  I type in smb://<ip address of windows box> and it asks me for a password.  ?  The password on the windows box?  There isn't one, or it's blank.  I tried a few different password combination.  What is this?  How can I get past it/change it?

I checked out this [thread]("http://http://www.ubuntuforums.org/showthread.php?t=192281").  Is it what I'm after?  Please advise.

you need to make a password for your winbloz box or at least I would suggest it! are the usernames the same for your ubuntu box and your winbloz box? if not, then create a file called username.map and store it in /etc/samba/ and then refer to it in your smb.conf file. what it does is map your winbloz username to your ubuntu username. did you add a user to your smbpasswd file? that's done with sudo smbpasswd -a usernamehere, then it'll ask you for a password twice and from now on that's your samba username and password. i just used the same as my login name and password. also help to do sudo smbpasswd -e usernamehere, which enables that user for samba. let me know if you need any other help. i think there is a way to set this up without making winbloz have a password but I wouldn't suggest it and plus I don't know how to do it. here is a good how-to for slackware but it should be applicable to almost all distros, [http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:samba](http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:samba). good luck!

---

### Post by Steve S. on 2006-11-03
I should have just asked and posted first rather than doing all the searching that I did.  It's very discouraging when you have just one little question, and the answers you get are, "You have just one question?  Here is the answer to all the worlds problems listed out in thread form.  Enjoy!" and then you have to weed through everything to get your answer.  Such is Linux sometimes, though.:D 

Your answer, dannyboy, was a breath of fresh air...exact answer to what I asked.  Thank you so much...I'll try it tonight and post if it fixes the problem.  Either way, thanks for the succinct answer! :-D

---

### Post by Steve S. on 2006-11-04
Argh!  Again!

I couldn't even get to your suggestion, dannyboy!  I can't even ping it now!

I checked ipconfig on the Windoze box, and it was different (thought it was set)!

So, I tried to ping the new address, no go.  I ping the gateway, and it goes through.

What do I do now?  On this box (Ubuntu box, ubox) I also have windoze, and the windoze from ubox to the family pc (fampc) is great, can print, share files, etc.  I just can't read the fampc files from Ubuntu on the ubox.  Do I restart samba or something?  According to synaptic I have samba and it's all set up, but I haven't messed with changing any of the files.  Does anyone have a thread they recomend?  I just want to be able to read the fampc files via Ubuntu on the ubox.  I don't care if fampc can read ubox files, just want Linux to be able to read fampc.

Also, I want to be able to print on the printer attached to the ubox when I'm using the fampc.  I can do that Windoze to Windoze, but not fampc Windoze to Ubuntu on the ubox!  Anyone have advise or a thread they recomend for that?  This is driving me nuts! :-k ](*,) 

Everyone confused?  On ubox, I have dual boot Ubuntu and Windoze.  On fampc, just Win.  I want to be able to print from fampc via the printer on the ubox when Ubuntu is running on ubox.  I also would like Ubuntu to be able to read the files on the fampc.  That's probably clear as mud, but I hope it helps clarify a little.

---

### Post by dannyboy79 on 2006-11-04
> **Steve S. said:**
> Argh!  Again!

I couldn't even get to your suggestion, dannyboy!  I can't even ping it now!

I checked ipconfig on the Windoze box, and it was different (thought it was set)!

So, I tried to ping the new address, no go.  I ping the gateway, and it goes through.

What do I do now?  On this box (Ubuntu box, ubox) I also have windoze, and the windoze from ubox to the family pc (fampc) is great, can print, share files, etc.  I just can't read the fampc files from Ubuntu on the ubox.  Do I restart samba or something?  According to synaptic I have samba and it's all set up, but I haven't messed with changing any of the files.  Does anyone have a thread they recomend?  I just want to be able to read the fampc files via Ubuntu on the ubox.  I don't care if fampc can read ubox files, just want Linux to be able to read fampc.

Also, I want to be able to print on the printer attached to the ubox when I'm using the fampc.  I can do that Windoze to Windoze, but not fampc Windoze to Ubuntu on the ubox!  Anyone have advise or a thread they recomend for that?  This is driving me nuts! :-k ](*,) 

Everyone confused?  On ubox, I have dual boot Ubuntu and Windoze.  On fampc, just Win.  I want to be able to print from fampc via the printer on the ubox when Ubuntu is running on ubox.  I also would like Ubuntu to be able to read the files on the fampc.  That's probably clear as mud, but I hope it helps clarify a little.

ok, i don't know what exactly you're talking about? why wouldn't you be able to do what I informed you to do? and what do you mean that you went to windows to see what the ip was for ubuntu? to find out what the ip is in ubuntu you type ifconfig. you need to do what i said and then it should work. also, are all your computer's in the same workgroup? is you ubuntu box dhcp or static ip? you also need to edit your smb.conf file so that the workgroup matches your other winbloz box but i thought you alread did that according twhat you said in your first thread. go tho this website for samba setup help: [http://www.ubuntuforums.org/showthread.php?t=198221&highlight=samba+help](http://www.ubuntuforums.org/showthread.php?t=198221&highlight=samba+help)

i would suggest you learn how to use the search feature within this forum because that's where i found the answer.

---

### Post by Steve S. on 2006-11-05
> **dannyboy79 said:**
> ok, i don't know what exactly you're talking about? why wouldn't you be able to do what I informed you to do? and what do you mean that you went to windows to see what the ip was for ubuntu? to find out what the ip is in ubuntu you type ifconfig. you need to do what i said and then it should work. also, are all your computer's in the same workgroup? is you ubuntu box dhcp or static ip? you also need to edit your smb.conf file so that the workgroup matches your other winbloz box but i thought you alread did that according twhat you said in your first thread. go tho this website for samba setup help: [http://www.ubuntuforums.org/showthread.php?t=198221&highlight=samba+help](http://www.ubuntuforums.org/showthread.php?t=198221&highlight=samba+help)

i would suggest you learn how to use the search feature within this forum because that's where i found the answer.


Thanks, dannyboy.  No, I checked Windoze for it's ip address, not Ubuntu's.  I checked Ubuntu's by using ifconfig.  I'll re-evaluate that thread...I've used a few threads but they haven't gotten me what I need.  Even though I search all right, apparently I sometimes don't get the parameters right and it's good to get someone else's perspective, a la yourself.  Thanks for finding the thread.

One thing I did note is that both computers are set to be dhcp.  Do I set the static ip address in the same place?  Is that what I should be doing rather than dhcp?

I'll check the thread and try your suggestion today.  Thanks again.

---

### Post by Steve S. on 2006-11-05
Oh, and the reason I didn't get to the password suggestion the other day is that it wasn't asking me for passwords anymore, so I'm missing something else.

As far as searching goes, I had followed [this ]("http://www.ubuntuforums.org/showthread.php?t=278034&highlight=connect+to+windows+network")and [this]("http://www.ubuntuforums.org/showthread.php?t=202605") prior to posting this thread.  Now, when I try to mount the file via the gui it acts like it's trying to find the file, then stops and nothing happens.  When I open the network file browser, it shows the windows network, but doesn't have any files in it.

I'll go through your slackware link now, dannyboy.  Thanks for the lead.

---

### Post by Steve S. on 2006-11-05
Well, two steps forward, one step back.

I was finally able to get CUPS to add a printer via the browser interface.  It seems administrative priveledges were disabled for dapper (see [here]("http://www.kdedevelopers.org/node/2117/")) and I had to weed through this thread and a couple of others to find out that there were two lines I needed to run in order for me to be able to enter my own user name and password to get CUPS to accept a new printer.
```
adduser cupsys shadow 
adduser joe lpadmin 
```
...where "joe" is your username.  It was just a blast to find that!:rolleyes: 
Now, I was able to add a network printer and print from it via the ubuntu box.  However, Windows sees that I at least have an Ubuntu box, but it can't see a printer on it or any files via samba.  How to fix that?  Either Windoze is not configured right or I haven't set the Ubox printer to share correctly.  Advise?

As far as reading the files goes, I ping from the ubox (after going to the windoze computer and re-confirming the ip address) and it won't ping it.  I can get in through the gateway, but that is it.  No Samba front-end that I use can see the Windoze files.  Please advise...what samba file can I show you to help figure this out?

And, dannyboy, apparently my knowledge of Linux is less than yours, 'cause I couldn't go through that how to slackware.  For example, the first thing I entered ```
groupadd smbguest 
``` returned ```
groupadd: unable to lock group file
``` and since that was the first thing in the how-to, I knew I was in trouble.  Should I correct this then proceed?  How can I correct this?

Sorry I'm being such a pain in the butt, but this is hardest thing I've done with Ubuntu yet...just can't seem to get it to go.

---

### Post by Steve S. on 2006-11-05
Oh, look out...we got it!  Well, no printer just yet, but we are closer each step.

Re-did [this one]("http://www.ubuntuforums.org/showthread.php?t=202605"), then did [this one]("http://www.ubuntuforums.org/showthread.php?t=278034&highlight=connect+to+windows+network"), especially the part about mounting via the gui, and we are good to go.

So, to summarize: I now can read the files on the family windoze pc (yeah!) from the ubunutu box (half the job!).  I can't yet do two things:
1. Print from the family windoze pc on the Ubuntu printer.  It (familypc) sees the U-box, but no printer and no files.
2. Look at files that are on the U-box from the familypc (not a big deal, but might come in handy).

Any help you can give would be great.

---

### Post by Steve S. on 2006-11-05
And it seems the final piece of the puzzle has been found.

I now have the ability to print to the Ubuntu box from the Windows box.  I can see the files from each computer of the other computer, just like I want.

It had seemed that the hinderance was from the Windows side so I went there.  I checked [this site]("http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html") and followed these instructions and changed the file adding my linux box ip address followed by the host name of the linux box as an extra line at the bottom.

```
Another common step is to ensure that hostname broadcast by
 CUPS is accessible from the Windows XP machine.  If your CUPS
 machine is accessible using a name rather than just an IP
 address then you don't need to do anything for this step.  If
 the CUPS machine is not accessible via it's hostname then you
 need to set a mapping between the CUPS hostname and its IP
 address in the Windows hosts file.  Under WindowsXP the host
 file is in C:\WINDOWS\SYSTEM32\DRIVERS\ETC\HOSTS, in Win2k
 replace WINDOWS with WINNT.  The format is simple:

# Example hosts entry
192.168.0.3 rock

Under some CUPS server configurations you will be able to use the
 IP address instead of the hostname, but often only a hostname
 will work.
```

Everything opened up and suddenly the Windows familypc could see the Ubuntu box.

Thanks for the leads, dannyboy.  All's good.

---

### Post by dannyboy79 on 2006-11-06
i am glad you got it!

---

### Post by Steve S. on 2006-11-06
Dannyboy, you still out there?  Or whomever else wants to brave the question.

Well, I clicked on my icon from the ubuntu box today and no connection.  Checked my firewall (firestarter) and sure enough, the ip address on the Windoze box is different at this start up, and firestarter caught it.

I changed the exception on the firewall and connection worked great, icon worked great, etc.

So, firestarter has to have the exception in there and/or there has to be a fixed ip address on the Windoze box.

How can I do that?  It is a Linksys router and both the U-box and the Windoze share the same router and each use Linksys (ubox has a pci card and canetenna and Windoze has usb linksys).  For some reason the ubox has a fixed ip (well, it never changes for some reason) but the other one changes.

How do I correct this without disturbing (read: screw up) the connection?

---

### Post by dmizer on 2006-11-06
please try the link in my sig for mounting samba shares.  it will work in kubuntu, and it will allow  you to mount the share by netbios name so you won't have to worry about the windows box ip changing.

edit: by the way, it's normal for ip addresses to change in a dhcp network.  a dhcp ip address is leased to a device for a certain amount of time, then the dhcp is renewed.  if there is a lower ip address avalable for the machine to take at this time, then it will.

---

### Post by Steve S. on 2006-11-06
> **dmizer said:**
> please try the link in my sig for mounting samba shares.  it will work in kubuntu, and it will allow  you to mount the share by netbios name so you won't have to worry about the windows box ip changing.

edit: by the way, it's normal for ip addresses to change in a dhcp network.  a dhcp ip address is leased to a device for a certain amount of time, then the dhcp is renewed.  if there is a lower ip address avalable for the machine to take at this time, then it will.

Um, well, actually, dmizer, thanks, but your thread is what has gotten me thus far.  I'm well versed in it as I've done it twice and got it right finally the second time.  Everything works great as I mentioned!  Thanks! :-D 

However, mounting samba isn't my problem at this point (or doesn't seem to be), it's the fact that my firewall blocks that ip address so the whole process seems to become null and void.  As soon as I kill the firewall or set the current ip address as an exception to the firewall, it let's it in and everything works great again.

So, how can I work around this and still allow firestarter to work?  Or, should I use a different firewall?  Or, is there something to be done in the samba config?  Or, is there something I'm missing?

---

### Post by dmizer on 2006-11-07
ah ... i see.  sorry for the mistake.

actually ... to start off, firestarter isn't a firewall.  iptables is your firewall, and iptables is installed on ubuntu by default.  firestarter is simply a gui front end which allows you to configure iptables more easily.

but i'm confused.  if you have a router (which you seem to), then why are you using firestarter to block local network traffic?  i used firestarter to configure my network for network address translation (internet connection sharing), but i have all traffic on the local network set to allow.  unless you have someone on your local network you don't trust, i don't see why you should have network traffic blocked.

---

### Post by dannyboy79 on 2006-11-07
well, i believe there is a way for most routers to still have dhcp but have your router so that it will reserve a certain ip for a particular mac address, so go into the config page for your router and look for something that states ip reservation, or for my netgear, I go to the link that states connected devices, then I see which computer is the one I want, then I click on it and say reserve this ip for this mac address so that the dhcp server wil only hanf out that ip for that computer in your case the winbloz box. or just go into winbloz and set it to be a static ip, that's very easy, under settings, then network connections, themn click on it, then click on properties, then look for anything that says, tcp/ip and click on properties, and then you can change it from get automatically to static, you'll want to first find out what your isp's dns server's are and then of course the ip you want the computer to use. you can normally find out the dns servers by going into the routers config and look at details or connection info something like that. either solution shuold work, let me know if you still need help.

---

### Post by Steve S. on 2006-11-07
Oh, wow.  Thanks to both of you for your quick response, although I just think dannyboy wrote the longest sentence I have ever seen.;) (JK)

Couple of things and that may help me iron out what I should do.

Dmizer: Ok, how do I set firestarter to allow local traffic.  Yes, you are right, I have no problem allowing local traffic and didn't know I was resticting it, although obviously I am.  So how can I correct that?  That should take care of the problem.

Dannyboy: On the Winbloze computer it is using the Linksys software to take care of setting the address and what-not.  I've found that if I use the Winbloze Zero configuration thing then it kills the signal (continuous scanning and all that).  Then I set the Linksys thing to be a static ip and it killed the signal.  Set it back to dhcp and it worked again.

But, as I mentioned to dmizer, I think allowing local traffic will take care of the problem, if I can get that set up.  Say our prayers and all that...

---

### Post by dannyboy79 on 2006-11-07
> **Steve S. said:**
> Oh, wow.  Thanks to both of you for your quick response, although I just think dannyboy wrote the longest sentence I have ever seen.;) (JK)

Couple of things and that may help me iron out what I should do.

Dmizer: Ok, how do I set firestarter to allow local traffic.  Yes, you are right, I have no problem allowing local traffic and didn't know I was resticting it, although obviously I am.  So how can I correct that?  That should take care of the problem.

Dannyboy: On the Winbloze computer it is using the Linksys software to take care of setting the address and what-not.  I've found that if I use the Winbloze Zero configuration thing then it kills the signal (continuous scanning and all that).  Then I set the Linksys thing to be a static ip and it killed the signal.  Set it back to dhcp and it worked again.

But, as I mentioned to dmizer, I think allowing local traffic will take care of the problem, if I can get that set up.  Say our prayers and all that...


I am confussed here, you have already said, "it's the fact that my firewall blocks that ip address so the whole process seems to become null and void. As soon as I kill the firewall or **set the current ip address as an exception to the firewall**, it let's it in and everything works great again." Based on that, you want your winbloz box to have the same ip it's always going to have so that your firewall let's it thru, isn't that correct??? You already know how to change settings in firestarter so why are you asking how to do this???? There's basically 2 ways to solve this, leave your firewall the way you had it based on when you made this statement, "it's the fact that my firewall blocks that ip address so the whole process seems to become null and void. As soon as I kill the firewall or **set the current ip address as an exception to the firewall**, it let's it in and everything works great again and just make sure that either you reserve and address for winbloz within your router config (this is STILL dhcp, we're not changing the fact that your router gives out ip addresses) we're simply telling the router, hey, if you see this mac address, give it this ip. OR you can configure firestarter to allow all incoming traffic from say 192.168.0, keeping in mind that I am guessing this is the first 3 sections of your lan ip addresses so if your lan's ip's are say, 192.168.1.blah then you would allow all incoming traffic from 192.168.1. Here is a thread on configuring iptables, which is the real firewall, firestarter is merely a gui to run it. [http://www.ubuntuforums.org/showthread.php?t=57111](http://www.ubuntuforums.org/showthread.php?t=57111)

---

### Post by Steve S. on 2006-11-07
> **dannyboy79 said:**
> I am confussed here, you have already said, "it's the fact that my firewall blocks that ip address so the whole process seems to become null and void. As soon as I kill the firewall or **set the current ip address as an exception to the firewall**, it let's it in and everything works great again." Based on that, you want your winbloz box to have the same ip it's always going to have so that your firewall let's it thru, isn't that correct??? You already know how to change settings in firestarter so why are you asking how to do this???? There's basically 2 ways to solve this, leave your firewall the way you had it based on when you made this statement, "it's the fact that my firewall blocks that ip address so the whole process seems to become null and void. As soon as I kill the firewall or **set the current ip address as an exception to the firewall**, it let's it in and everything works great again and just make sure that either you reserve and address for winbloz within your router config (this is STILL dhcp, we're not changing the fact that your router gives out ip addresses) we're simply telling the router, hey, if you see this mac address, give it this ip. OR you can configure firestarter to allow all incoming traffic from say 192.168.0, keeping in mind that I am guessing this is the first 3 sections of your lan ip addresses so if your lan's ip's are say, 192.168.1.blah then you would allow all incoming traffic from 192.168.1. Here is a thread on configuring iptables, which is the real firewall, firestarter is merely a gui to run it. [http://www.ubuntuforums.org/showthread.php?t=57111](http://www.ubuntuforums.org/showthread.php?t=57111)

Oh, ok.  Thanks for the thread since that is probably what I'll mess with.

But allow me to clarify: if I turn both computers on, I can set the exception for what the ip address is on the Winbloze computer for THAT CURRENT LOG IN.  I don't know how to make a blanket exception and say,"Accept **all** local ip addresses." I only know how to do each individual ip address as it occurs.  I hope that makes some sense.  So, right now I have like 3 exceptions, but I have to set each one as it occurs/each time I log on and the ip address is changed on the Winbloze pc.

I guess I don't have to have a static ip address for the Winbloze box as long as firestarter let's the local ip addresses through.

So, I'll read the thread and set the iptables.

---

### Post by dannyboy79 on 2006-11-07
> **Steve S. said:**
> Oh, ok.  Thanks for the thread since that is probably what I'll mess with.

But allow me to clarify: if I turn both computers on, I can set the exception for what the ip address is on the Winbloze computer for THAT CURRENT LOG IN.  I don't know how to make a blanket exception and say,"Accept **all** local ip addresses." I only know how to do each individual ip address as it occurs.  I hope that makes some sense.  So, right now I have like 3 exceptions, but I have to set each one as it occurs/each time I log on and the ip address is changed on the Winbloze pc.

I guess I don't have to have a static ip address for the Winbloze box as long as firestarter let's the local ip addresses through.

So, I'll read the thread and set the iptables.

alright, i'll make it way easier on ya, tell me what the model number of your router is and I'll help you set it up so that you winbloz box gets the same ip each time and youo won't have to make winbloz a static ip but it will be static because the router will give it the same ip based on it's mac address. if you want my help that is.

---

### Post by Steve S. on 2006-11-07
> **dannyboy79 said:**
> alright, i'll make it way easier on ya, tell me what the model number of your router is and I'll help you set it up so that you winbloz box gets the same ip each time and youo won't have to make winbloz a static ip but it will be static because the router will give it the same ip based on it's mac address. if you want my help that is.

Good man (I'm assuming)!  I will probably take you up on that.

Let me check it later on today and I'll post again.  Thanks!

---

### Post by dmizer on 2006-11-07
actually ... just go to this link: [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

look under the section entitled: "How do you specify a range of IPs or use wildcards in the rules?"

so when you add your exception, you will have to add it in [CIDR]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing) format. it will look something like this:
> 192.168.1.1/24
the above will allow connections on all ip's from 192.168.1 - 192.168.1.254 on the 255.255.255.0 subnet

---

### Post by Steve S. on 2006-11-07
Well, up and down again...I'm really loving this.

(this is all from the Ubox, Ubuntu box)
I had mounted a folder after using dmizer's [link here ]("http://www.ubuntuforums.org/showthread.php?t=202605")initially then using the gui settup mentioned [here]("http://www.ubuntuforums.org/showthread.php?t=278034&highlight=connect+to+windows+network").  When I tried the folder today, nothing.  Shut the firewall off, NOTHING.  Ok, that's new; up to this point only the ip address confusion with the firewall had been the hinderance.  I turned the firewall back on and set up dmizer's suggestion, but of course there was still nothing in that folder (error message...wouldn't open; "Folder contents could not be displayed.").  I pinged the Winbloze box and it went through fine (the firewall thing works!) but still no contents in the folder.

(then, sitting at the Winbloze box)
I tried to print to the Ubox.  Worked fine, although still slow (any way to fix that?...one thing at a time).  I tried to look at files on the ubox: worked fine.  So, everything good on this end.

(back to ubox)
But what the crap is going on here?  How do I check this?

---

### Post by dmizer on 2006-11-08
again, firestarter is NOT your firewall.  it's just a gui front end used to configure iptables.  once iptables are configured, they are ALWAYS running.  this means that even if you close firestarter, your firewall is still running just as you configured it before.

ps. the guide you linked to is not mine, it's stormbringer's ... but thanks anyway ;)

furthermore ... samba is a server only.  so keep this in mind:
this: [COLOR="SeaGreen"]windows box ----> samba[/COLOR]
but not: [COLOR="Red"]windows box <---- samba[/COLOR]
and not: [COLOR="Red"]windows box <----> samba[/COLOR]

now ... if you want this:
ubuntu ----> windows box

you'll need to use something like cifs.  the howto for configuring cifs is the third link in my signature.

---

### Post by Steve S. on 2006-11-08
> **dmizer said:**
> again, firestarter is NOT your firewall.  it's just a gui front end used to configure iptables.  once iptables are configured, they are ALWAYS running.  this means that even if you close firestarter, your firewall is still running just as you configured it before.

ps. the guide you linked to is not mine, it's stormbringer's ... but thanks anyway ;)

furthermore ... samba is a server only.  so keep this in mind:
this: [COLOR="SeaGreen"]windows box ----> samba[/COLOR]
but not: [COLOR="Red"]windows box <---- samba[/COLOR]
and not: [COLOR="Red"]windows box <----> samba[/COLOR]

now ... if you want this:
ubuntu ----> windows box

you'll need to use something like cifs.  the howto for configuring cifs is the third link in my signature.

Yeah, I know the link I mentioned wasn't yours, but I gave you credit on providing it...:) 

I'll check out the cifs thread.  But why did my wanting to view the windoze box work occasionally?

---

### Post by dmizer on 2006-11-08
> **Steve S. said:**
> But why did my wanting to view the windoze box work occasionally?

some recent updates have changed the way nautilus and other programs like smbfs mount and view network shares.  it took me some time to nail down exactly how to get around the issue.

---

### Post by dannyboy79 on 2006-11-08
> **dmizer said:**
> again, firestarter is NOT your firewall.  it's just a gui front end used to configure iptables.  once iptables are configured, they are ALWAYS running.  this means that even if you close firestarter, your firewall is still running just as you configured it before.

ps. the guide you linked to is not mine, it's stormbringer's ... but thanks anyway ;)

furthermore ... samba is a server only.  so keep this in mind:
this: [COLOR="SeaGreen"]windows box ----> samba[/COLOR]
but not: [COLOR="Red"]windows box <---- samba[/COLOR]
and not: [COLOR="Red"]windows box <----> samba[/COLOR]

now ... if you want this:
ubuntu ----> windows box

you'll need to use something like cifs.  the howto for configuring cifs is the third link in my signature.

I'll have to disagree here, Samba was created by reverse engineering microsoft file sharing, when you install samba and configure it properly, winbloz xp and ubuntu can share files over samba just fine. I should know, that's how my winbloz xp and ubuntu box share files.

---

### Post by dmizer on 2006-11-08
samba is the server
smbfs is the connector.
cifs is the replacement for smbfs

they are two different packages, and definitely differnet components.

so with that in mind:
this: windows box ----> samba
this: ubuntu + cifs ----> windows box
this: ubuntu + smbfs ----> windows box
never: samba ----> windos box

what i'm trying to stress here is that even though you've configured smb.conf on your ubuntu box, this does not mean that you will be able to connect from your ubuntu machine to your windows box.

also, and possibly an interesting side not to you.  is that _you don't need to install samba_ to connect to a windows machine. all you have to do is install smbfs (which includes cifs).  this is how i do it at work ;)

---

### Post by dannyboy79 on 2006-11-08
> **dmizer said:**
> what i'm trying to stress here is that even though you've configured smb.conf on your ubuntu box, this does not mean that you will be able to connect from your ubuntu machine to your windows box. 

Yes it does, smbfs is for mounting windows shares to your linux box, not for being able to connect and access files from winbloz. Im not sure what you're doing wrong but this is the case for me, i simply had to share a folder within winbloz xp, ensure there was a username and password on winbloz that matched the username and password on my ubuntu box, installed samba (which according to the samba website; Samba includes the front-end tools that are used to manage smbfs-based file service connections.) I then ensured that my samba setup had the same workgroup in it's smb.conf, also encrytped passwords since that's what winbloz xp uses, then on my ubuntu box I simply said connect to server under places and I typed in smb://servername/share and I was sharing files. Of course samba is a server. Winbloz has a server built-in also, which samba was copied from based on SMB/CIFS Protocol.

> **dmizer said:**
> also, and possibly an interesting side not to you.  is that _you don't need to install samba_ to connect to a windows machine. all you have to do is install smbfs (which includes cifs).  this is how i do it at work ;) 

correct, but he wants to share back and forth, not just 1 way.

---

### Post by Steve S. on 2006-11-08
> **dannyboy79 said:**
> Yes it does, smbfs is for mounting windows shares to your linux box, not for being able to connect and access files from winbloz. Im not sure what you're doing wrong but this is the case for me, i simply had to share a folder within winbloz xp, ensure there was a username and password on winbloz that matched the username and password on my ubuntu box, installed samba (which according to the samba website; Samba includes the front-end tools that are used to manage smbfs-based file service connections.) I then ensured that my samba setup had the same workgroup in it's smb.conf, also encrytped passwords since that's what winbloz xp uses, then on my ubuntu box I simply said connect to server under places and I typed in smb://servername/share and I was sharing files. Of course samba is a server. Winbloz has a server built-in also, which samba was copied from based on SMB/CIFS Protocol.

...which may be the key in how the Ubox is looking at the Windoze files.  I used Windows Share as the option within the gnome gui under Connect to Network.  My Linux guy here at work stopped by and he mentioned that I should use Samba rather than Windows Share option.

So, I'll try that tonight and see what we come up with.  It may save me the effort doing dmizer's thread (although I'm sure cifs would work ;-).  If I can't get it to go from there, I may post again or try cifs.

---

### Post by dannyboy79 on 2006-11-08
if you're talking about when you go under settings, then administration, then shared folders, and you click on a folder to share and put a check mark for windows shareing, then that is activating it for samba. so if it isn't working than you have another problem. have you done what I suggested way back in the way begining? about the usernames and passwords being the same, etc etc???

---

### Post by Steve S. on 2006-11-08
I did most of your original post a while back, dannyboy.  Sorry I didn't explain that before.

> you need to make a password for your winbloz box or at least I would suggest it! are the usernames the same for your ubuntu box and your winbloz box? if not, then create a file called username.map and store it in /etc/samba/ and then refer to it in your smb.conf file. what it does is map your winbloz username to your ubuntu username. 

I didn't do this, but the Winbloze box does have it's own password, now.  I don't know how to have it referred to in the smb.conf file.

> did you add a user to your smbpasswd file? that's done with sudo smbpasswd -a usernamehere, then it'll ask you for a password twice and from now on that's your samba username and password. i just used the same as my login name and password. also help to do sudo smbpasswd -e usernamehere, which enables that user for samba. 

I did do all of this early on...it is also in the thread dmizer was originally talking about.

> if you're talking about when you go under settings, then administration, then shared folders, and you click on a folder to share and put a check mark for windows shareing, then that is activating it for samba.

I wasn't, but if I look there it only has the file that I want the Winbloze box to see on the Ubox.  This was also in the thread dmizer mentioned (you guys are on the same wavelength on a lot of this).

I was talking about going to places>connect to network>then selecting Windows share and setting it up from there, which is what I did and is now working, although seemingly sporadically.

Interestingly enough, it is working right now from the log in/right away.  So, I don't really have a problem to fix right now; it's working just as I want.

Let's hope it continues to work this way.  If so, all of y'all's work has been hugely and greatly appreciated.  Well, it's appreciated even if I have to post in the future 'cause it's not working for some reason...that odd glitch that showed up the other day and now is apparently gone (the same thing dmizer is talking about?)

So, a hearty thanks to you both and I'll post again if I don't have the connection and we can debate whether it is my settup on the connection or if I need to add cifs (which, apparently I already have if I have smbfs, which I do).

Thanks again!

---

### Post by Steve S. on 2006-11-14
Well, you guys probably hate me and are tired of dealing with me at this point, but checked it just now and nothing...can't even get to it via Konqueror which I could do as a last resort before.

You recomend I go through the cifs instruction mentioned before?  Or anyone else want to take a stab at it?

---

### Post by dmizer on 2006-11-15
again please be aware:

changing smb.conf does NOTHING for connecting ubuntu to windows.  i think dannyboy's misudnerstood what you're wanting to do.

your fix is to use cifs as i inticated earlier.

---

### Post by dannyboy79 on 2006-11-16
cifs or smbfs is ONLY for mounting network shares to your ubuntu box, if you want to connect to your network thru nautilus or konquerer than you have to change your smb.conf to make it have the same workgroup etc. if you didn't do this, then your file browser would have no idea that you wanted it to show you shares in say, workgroup, LINUX, cause the default is MSHOME i believe. the thread subject states "Re: SAMBA Network Password" NOT anything about MOUNTING WINDOWS SHARES. Good luck Steve S, dmizer will get you setup so that you can just mount the share locally and then you'll be able to see it thru nautilus or konq, you'll then go to a local folder within your file system instead of going thru places, then connect to network share. his way is easier to set up.

---

### Post by dmizer on 2006-11-16
actually you don't have to do anything with smb.conf to set the workgroup.  nautilus and konq both have options to do that. can't remember how to do it with konq though.

but for some strange reason it never occured to me that the problem might be related to ubuntu not being in the same workgroup. ugh ... apologies dannyboy79.

---

### Post by Steve S. on 2006-11-16
> **dannyboy79 said:**
> cifs or smbfs is ONLY for mounting network shares to your ubuntu box, if you want to connect to your network thru nautilus or konquerer than you have to change your smb.conf to make it have the same workgroup etc. if you didn't do this, then your file browser would have no idea that you wanted it to show you shares in say, workgroup, LINUX, cause the default is MSHOME i believe. the thread subject states "Re: SAMBA Network Password" NOT anything about MOUNTING WINDOWS SHARES. Good luck Steve S, dmizer will get you setup so that you can just mount the share locally and then you'll be able to see it thru nautilus or konq, you'll then go to a local folder within your file system instead of going thru places, then connect to network share. his way is easier to set up.

Yeah, I know the thread name started with the password thing, but it has mutated over time...thanks for your help, and sorry for all the hassle I've caused you guys.

I had already changed smb.conf regarding the workgroup some time ago.

Should I run through the cifs how-to?  Is that my best bet at this point?

---

### Post by Steve S. on 2006-11-19
dmizer, I'm going through your cifs how-to (looks pretty good) but it hangs on me right after I install winbind.  It says: "Starting winbind daemon winbind" then just sits there for hours.

Ideas?

Edit: and now anytime I try to run Synaptic or try to sudo aptitude update, or install anything, it says:
 ```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
```

What's that about?  Then I manually run it as it says and it says the same "Starting winbind daemon winbind" then just sits there forever.

---

### Post by dmizer on 2006-11-19
well there's a first.  no idea what could have caused that.

try:
```
sudo dpkg --configure -a
```
were there any other errors durning the install of winbind?

---

### Post by Steve S. on 2006-11-20
> **dmizer said:**
> well there's a first.  no idea what could have caused that.

try:
```
sudo dpkg --configure -a
```
were there any other errors durning the install of winbind?

Yeah, that's what I was running.  That's what started winbind and just left it running.

I don't know of any other errors.  Where could I look?

---

### Post by dmizer on 2006-11-20
you don't happen to be low on disk space are you?

this error only occurs when apt is quit unexpectedly before it's completed.  maybe you got a corrupt download or install of winbind somehow, or apt quit because it was out of space to compile.

now to fix it ...

browse to /var/lib/dpkg/updates ... if there is something in this directory, do this:
```
sudo rm /var/lib/dpkg/updates/*
```
use synaptic to reinstall winbind.

---

### Post by Steve S. on 2006-11-20
> **dmizer said:**
> you don't happen to be low on disk space are you?

this error only occurs when apt is quit unexpectedly before it's completed.  maybe you got a corrupt download or install of winbind somehow, or apt quit because it was out of space to compile.

now to fix it ...

browse to /var/lib/dpkg/updates ... if there is something in this directory, do this:
```
sudo rm /var/lib/dpkg/updates/*
```
use synaptic to reinstall winbind.

Excellent, will do.  No, not low on disk space (about 20 gigs remaining) but the corrupt download may be possible.  I did quite the "running winbind daemon winbind" thing but that is all I quit.  Thanks.

---

### Post by Steve S. on 2006-11-20
Ok, I did everything you said.  It corrected the problem fine, it seems.  Can use Synaptic again and it updates and all that.

But when I removed winbind then reinstalled it, it stuck at the starting winbind daemon again.  I'm attaching a jpg.

It sat there for about 6 hours.  Should it take longer than this?  Do I need to let it sit longer?  Please help.

Edit: I just noticed something.  I have tor and privoxy running, but it hasn't worked the last couple of days.  I was messing with that after the six hours of the winbind thing, repaired winbind as you mentioned above, removed winbind then sudenly tor started working fine.  Related?

If not, just an interesting note.

---

### Post by dmizer on 2006-11-21
it should start immediately.  did you modify nsswitch.conf before installing winbind?

---

### Post by Steve S. on 2006-11-21
> **dmizer said:**
> it should start immediately.  did you modify nsswitch.conf before installing winbind?

By adding "wins"?  Yep.

---

### Post by Steve S. on 2006-11-21
Here are the contents of my nsswitch.conf:
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns mdns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

### Post by dmizer on 2006-11-21
do you have samba installed ... and if so, have you done anything to smb.conf?

---

### Post by Steve S. on 2006-11-21
Well, I'll have to change some passwords now, I guess,  ;-) but here is my /etc/samba/smb.conf:
```

[global]
    ; General server settings
    netbios name = garageubuntu
    server string =familypc
    workgroup = SCHULTZ_HOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 
    interfaces = lo, eth0, ra0
    bind interfaces only = true

SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = stephen
    force group = stephen
available = no
public = no
writable = no

```

Edit: 
I just noticed the line that said "wins support = no" and changed the no to "yes."  Didn't know if that would matter or not, so am giving it a shot.  Rebooted and am now running Winbind in synaptic.  Well, it didn't fix it right away, but I'll give it a couple of minutes...maybe.

Of course, since I don't know what I'm talking about, that may have no effect at all...;-)

Eit again:
No dice, as you might have guessed.  I have left that line changed to "yes" though.  Should I leave it that way?

---

### Post by dmizer on 2006-11-21
alright ... i give up on winbind for you.  i don't know what the deal is preventing you from making it work.  i don't see anything there that should prevent it. possibly could be firewall settings, but i really don't know.  my suggestion is to simply remove it with synaptic.

so in your case, you're just going to have to use ip addresses instead of netbios name ... sorry.  so where it says "netbiosname" in the howto, just enter the ip address of the computer you're trying to connect to.

also, you'll have to return wins support to "no" if you have a dhcp network.

---

### Post by Steve S. on 2006-11-21
Since the network is dhcp, the ip adress isn't static.  Do I enter it like a range as I did in the firewall settup we discussed before?

---

