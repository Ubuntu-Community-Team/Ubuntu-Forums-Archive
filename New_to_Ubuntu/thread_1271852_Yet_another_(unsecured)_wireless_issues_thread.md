---
title: "Yet another (unsecured) wireless issues thread"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2009-09-21
I have no problem connecting to unsecured wireless networks from within windows, and I can connect to secured connections in both windows and jaunty, but I can't connect to unsecured networks with jaunty (usually).

My campus uses several secured wireless networks that students don't have access to.  They also have a campus wide SSID called Butte_College that is unsecured and students can use.  They handle security on the unsecured network by making you log in through a web browser before you can do anything on the network.

Well from some locations on campus I can connect to the unsecured network either on my first try or by first trying to correct to a secured network with the wrong password then trying the unsecured one.  However, there are parts of campus where I can't really connect to the unsecured networks with jaunty (though I have no problems in windows at those locations).  I did an iwconfig wlan0 scan and it turned up several 'cells' that had an SSID of Butte_College.  Is ubuntu having trouble determining which one it should actually connect to and just running in circles?  I was able to connect a few times this morning for all of 2 minutes before it disconnected again.

Now to further complicate things, I do most of my day to day stuff with an account that can't sudo.  I sort of regret setting myself up this way, so I'm fairly limited with what I can do on my main account as far as diagnosing stuff, but on my account that can sudo, it just connected no problem the first time.  Does anyone have any suggestions on what to try?  Is it possible that I'll need to be able to sudo to get on the unsecured access at school?  If so, is there a way I can change my main account so that I can sudo?  I've run out of time here on campus to mess with it this morning, and now am in windows so I can't try anything else right now, but I am running a sony VAIO PCG-K15 laptop.

Hopefully someone can help me.

---

### Post by swoody on 2009-09-21
Well since you can connect with a sudoer account, but not a standard user, this sounds like a permissions issue. You may want to make sure you have enabled all networking/wireless permissions on your standard account. You should be able to do this in your sudoer account, by going to "System>Administration>Users & Groups" and checking around there for permission settings. Let us know if you can find it, or have any issues assigning the permissions.

---

### Post by diablo75 on 2009-09-21
It's quite possible (this being a college campus filled with people who don't want to pay to get on the Internet) that the times you have attempted a connection to the unsecured access point, and failed, might have been because the network was overwhelmed.  It's kind of like trying to log into the most popular chat room on yahoo, and while at a given moment it might look like there are a few slots available, by the time you actually connect, they've already filled up.  And if they've not been filled, they're in the process of being filled.

Now I know you say you've been able to connect to the network with Windows and only some of the time with Ubuntu... but I would venture a guess that of the times you actually got a connection in Windows, you weren't actually able to send and receive traffic; only associate with the wireless AP.  I was recently at a military base where there were a couple dozen solders all attempting to access a WEP secured network, which worked great until more than 20 attempted to access.  Those who already had a connection were in good shape, but others who connected after that weren't actually getting any network traffic to move so Internet browsing didn't work, even though it said they were connected.

So, while this might not be the answer you're hoping for, I'm going to put my money on the wireless AP's being overwhelmed with too many connections.

---

### Post by scared0o0rabbit on 2009-09-21
> **diablo75 said:**
> It's quite possible (this being a college campus filled with people who don't want to pay to get on the Internet) that the times you have attempted a connection to the unsecured access point, and failed, might have been because the network was overwhelmed.  It's kind of like trying to log into the most popular chat room on yahoo, and while at a given moment it might look like there are a few slots available, by the time you actually connect, they've already filled up.  And if they've not been filled, they're in the process of being filled.

Now I know you say you've been able to connect to the network with Windows and only some of the time with Ubuntu... but I would venture a guess that of the times you actually got a connection in Windows, you weren't actually able to send and receive traffic; only associate with the wireless AP.  I was recently at a military base where there were a couple dozen solders all attempting to access a WEP secured network, which worked great until more than 20 attempted to access.  Those who already had a connection were in good shape, but others who connected after that weren't actually getting any network traffic to move so Internet browsing didn't work, even though it said they were connected.

So, while this might not be the answer you're hoping for, I'm going to put my money on the wireless AP's being overwhelmed with too many connections.

Actually I posted the message from windows sitting at the exact same location after rebooting into windows, so I think that's not the case.  I suppose it's possible that it might have something to do with permissions, however I'm able to connect to the unsecured wireless network from other areas of campus without my sudoer account.  And, on the sudoer account I never performed a sudo to connect.  I only tried it once as I was running out of time, but when I switched accounts briefly to look at something, it hopped right on.  That's not to say that 3 minutes later it might have been booted off, but I didn't have time to check it.  I was able to actually connect to the unsecured network 3 times this morning sitting in the exact same spot on the non-sudoer account, but each time I could only stay connected about 5 minutes before it disconnected again.  During those 5 minutes everything worked great though.

The thing that leads me to believe that it may be having issues dealing with multiple access points with the same SSID is that I was sitting in the middle of campus where as where I normally have better luck I'm more on the far edge of campus.  Also, for a while before I installed ubuntu I played around with a live cd of kubuntu, and it has a different connection manager thing.  When I opened it up it seemed like it had a little radar of how good of signal I was getting from all the different access points.  On it, I could see many different access points with all the different names including several with the Butte_College ID.  I'm wondering if since I was on the edge of campus there was really only one it could reach, so it wasn't having a problem, but when I'm in the middle of campus and I tell it to connect to Butte_College it flips out because it doesn't know which one it should try?

---

### Post by SuaSwe on 2009-09-21
That sounds like a logical explanation to me! 

Do they all use the same encryption (down to the actual key)?

---

### Post by swoody on 2009-09-21
> **scared0o0rabbit said:**
> ... I suppose it's possible that it might have something to do with permissions, however I'm able to connect to the unsecured wireless network from other areas of campus without my sudoer account.  And, on the sudoer account I never performed a sudo to connect.
Well, permissions are a different deal from running a "sudo ...." command. Typically the sudoer account is also the Administrator account for the computer, and the one who sets/issues permissions for the rest of the users. The reason I suggested this may be an issue, is there's a permission you can set for users to either allow or deny them access for connecting to wireless networks. I figured this may be disabled for your standard account, and cause an issue when you attempt to connect to a wireless network. Obviously, this isn't the case, though, as you said you were able to connect several times with your standard account, but were then booted soon after.

Also, sorry about my assumption. I had thought from your first post that you were able to connect with no problems using the sudoer account:

> **scared0o0rabbit said:**
> ...but on my account that can sudo, it just connected no problem the first time.


> I only tried it once as I was running out of time, but when I switched accounts briefly to look at something, it hopped right on.  That's not to say that 3 minutes later it might have been booted off, but I didn't have time to check it.  I was able to actually connect to the unsecured network 3 times this morning sitting in the exact same spot on the non-sudoer account, but each time I could only stay connected about 5 minutes before it disconnected again.  During those 5 minutes everything worked great though.

You may want to speak to you school's IT department about this. If you are able to connect, but get repeatedly disconnected, there may be something built into their security that checks whether a device on the network is active/allowed or not in 5 minute intervals. If there's something along the lines of a temporary permission file that the network needs to store on your computer, or anything like that which requires Windows, it may not work the same on your Ubuntu computer. Then the network fails to find that permission file on your computer, and removes you from the network. Again, I'm not a networking guru by any means, so it would be best to speak to your school's IT department about this so you can find out exactly what is involved with their particular security setup.

> The thing that leads me to believe that it may be having issues dealing with multiple access points with the same SSID is that I was sitting in the middle of campus where as where I normally have better luck I'm more on the far edge of campus.

If you're looking for a program that will give you a better feel and control over multiple networks, you may want to try installing and using wicd. I find it very useful, and an improvement over the default network-manager. Like you mention, it has a signal strength indicator for each wireless network, and will allow you to choose the strongest one.

Now, have you had these issues connecting to *any* other wireless networks, either secured or unsecured? If you have not tested it out, you may want to bring your computer to different areas that offer free WiFi (Starbucks, library, Barnes & Noble, etc.) and test it out on other wireless networks. If you're only encountering this issue on your school's networks, again I'd recommend speaking with them directly about the issue. Chances are they can either give you advice about what is going on, or that they have heard other users with the same complaints, and will be able to confirm that it is an issue with the school's network.

Whew! Ok, sorry that dragged on so long, but hopefully this can get you headed in the right direction :) Try out what I mentioned above, and let us know what works/doesn't for you!

---

### Post by louieb on 2009-09-21
> **scared0o0rabbit said:**
> IIf so, is there a way I can change my main account so that I can sudo? 

System>Administration>Users and Groups : add the account to the Admin group.

---

### Post by scared0o0rabbit on 2009-09-21
> **louieb said:**
> System>Administration>Users and Groups : add the account to the Admin group.


After adding myself to the Admin group I get this when I try and sudo:

Sorry, user nicholas is not allowed to execute '/usr/bin/gedit' as root on nicholas-laptop.

Is there any other things I need to change also?  I checked to allow that user to administer the system in the user properties too.

So I installed wicd, which was an interesting process.  It uninstalled the default network manager as part of the process.  It makes it so there isn't a little icon up at the top anymore, which is only a minor annoyance, but I checked automatically connect (for my home network where I am now), and it connects to that just fine, but... when I try and open up wicd now it just sort of hangs.  The window stays open but blank for a while, and then just goes away.

So... I'm not really sure if I should try and re-install the default network manager because I'm not sure I'll be able to change the settings for my own network or for connecting on campus.  I'll try and restart and see if I can get it working right, but if not, is there another network management program I should try instead?

Edit:

So after a restart, wicd is showing up in the little bar along the top, it automatically connected to my network, and I can open it up and see statuses.  So I'll check to see if this makes things an easier to diagnose on wednesday when I'm on that part of campus again.

---

### Post by scared0o0rabbit on 2009-09-22
Well I was able to get online about 20 feet from where I was having trouble yesterday in the same open space in the same building, so I guess installing wicd seems to have done the trick.

---

### Post by t0p on 2009-09-22
> **scared0o0rabbit said:**
> Well I was able to get online about 20 feet from where I was having trouble yesterday in the same open space in the same building, so I guess installing wicd seems to have done the trick.

I'm pleased for you that wicd seems to have solved your problem.  But I'm a little confused by your descriptions of what was happening when you were using the default network manager and the kubuntu network manager.

I'm running Jaunty, and I use the default network manager.  When I click on the nm icon, up on my top panel, a window opens that contains a list of all the available connections; and each wireless connection has a bar next to it showing the "signal strength" of that particular access point.  Didn't nm work like that for you?  Couldn't you just select the AP you wanted to use and click on it?

The stuff you said about how you thought maybe the network manager was confused over which AP to use... surely if you clicked on a particular AP in the list, that's the AP it would connect to?  That's how it works for me anyway.

I hope wicd has solved this for you.  But I am baffled about what you described.

---

### Post by swoody on 2009-09-22
> **scared0o0rabbit said:**
> Well I was able to get online about 20 feet from where I was having trouble yesterday in the same open space in the same building, so I guess installing wicd seems to have done the trick.

Good! Glad to hear everything's working now :D

Well, it does seem odd that wicd solved your issues, but I've heard of *much* stranger things before ;)

Were you able to stay connected for a long period of time? Didn't experience any drops or other issues?

---

