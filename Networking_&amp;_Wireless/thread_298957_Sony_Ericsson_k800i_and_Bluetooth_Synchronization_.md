---
title: "Sony Ericsson k800i and Bluetooth Synchronization with Evolution"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by fotakis on 2006-11-13
Hello all,

I it is late right now, and I am going to bed. Giving you a heads up, tomorrow I will be writting my first little how to on the subject. "Synchronizing k800i with evolution via bluetooth". 

I would like to get a feel if there is enough requirement for this or if there is something else out there, and basically everybody can do it on their own, I for one only found bits and pieces. Please post a comment if you would like me to write the mini how-to

Best Regards,
Fotis

Edit:

[SIZE=6]**HOW-TO**[/SIZE]

Hello again,

I have some bad news and some good news for anyone interested.

Bad news first:
The synchronization with evolution doesn't exactly work. Specially in the contacts department, some of my contacts were duplicated after consecutive synchronizations and others were just removed, so this is a beware to anyone out there BACK UP FIRST!!!!.

Good News:
Well I am doing ok after the operation and I am back to fullfill my promise, and to write my very own, and very first howto :-)


**[SIZE=4] Disclaimer:[/SIZE]**

I would like to inform to all of you reading this to understand the following points:

1. I am a newbie, and by no means believe that this is the only way, nor the correct way to synchronize your phone.
2. What you will be reading is a collection of materials from other more experienced authors, whose websites I will publish, if I find them all.
3. Please don't hold me responsible if what I am saying doesn't work, just ask here and I will try to look for an answer for you.


**[SIZE=4] Mini-Newbie How-to:[/SIZE]**

**[SIZE=4] Intro:[/SIZE]**

So what we are tyring to do is to gather the tools already available to us to try an synch up our phones with evolution with the tools already available to us. This guide is intended for Edgy users, cause this is my first Linux Distro that I have actually been using for developments and as a Desktop for more that 3 weeks :-)!!!(I always ended up rebooting to windowz :-( )

Before going on, just know that if you plug your phone using a USB cable, and select Transfer Mode, you Phone Files will be readily available to you with no hasle.

**[SIZE=4] Requirements:[/SIZE]**

1. Know how to add repositories to your installation
2. Have a working bluetooth dongle.

[SIZE=4]** Steps:**[/SIZE]

1.) Make sure you have the multiverse and universe repositories enabled.

2.) From the command line:

#sudo apt-get install bluetooth bluez-pin bluez-utils multisync libmultisync* evolution-plugins

[I]When I run the above command I get the following error:
The following packages have unmet dependencies:
  libmultisync-plugin-palm: Depends: libpisock8 but it is not installable
E: Broken packages
[/I]

Don't worry about that, what we really need I thinkg is the irrc plugin.

The above should give a nifty little tool caled hcitool, this tool will be used to see if you can find your phone.

3.)Edit the file /etc/bluetooth/hcid.conf

This is what mine looks like.
```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        passkey "1234";
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;
        discovto 0;

        # Default link mode
        #   none   - no specific policy 
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;
}



```In the above script I set the security to auto.

You will need the pass key when you will pair your phone, so write it down somewhere

Run the command
4.) #sudo /etc/init.d/bluetooth   [COLOR=Red]<-- I don't know if this is really necessary, I have to do it though.[/COLOR]


Now make sure you have bluetooth on and visible on your phone.
Run.
5.) # hcitool scan

wait for a bit......

And this should come up.
[I]Scanning ...
        00:18:13:98:9A:0C       Pimp
[/I] Again make sure your bluetooth is plugged in, if the above didn't work.

The above information is the mac of the phone and the name you have set up on your phone. This information is showing you that you can see your phone.

Now for the interesting part.

6.) Open Multisynch from Applications-> Accessories-> Multisync

7.) Click on New...

8.) For the first plugin select "Ximian Evolution 2"
9.) For the second plugin select "IrMc Mobile Devices"

10.) Now click on the "Options.." button for your "IrMc Mobile Devices" 

11.)In the connection type select "Bluetooth"

12.) And click "Search For Units..." 

If you are lucky it will find your phone.

13.) After you have selected your phone from the List of Units, click on "Test Connection" .

This will cause YOUR phone to ask you if you want to pair with the computer, if you select "Yes" it will ask for a passphrase, use the one from step 3.

[I][SIZE=4][COLOR=Red]Note: When I tried this, I had to set a permanent pair between my phone and the computer, otherwise it will just not work.[/COLOR][/SIZE]

[/I]14.) Click OK
15.) Click OK again.

You should now have a new item in your multisync list.

16.) Cross Your Fingers
17.) Click on Sync

18.) You should now be seeing a synchronization message on your phone.


**[SIZE=4][COLOR=Black] Conclusion:[/COLOR][/SIZE]**

There you have, I hope somebody will help me correct many of the probable errors above, and make this a more consice and complete how-to.

[SIZE=5][COLOR=RoyalBlue] Cry For Help:[/COLOR][/SIZE]

There are several things I want to attempt to address on this post, so I am shoutinng out to users with a Sony Eriksoon on the same family as the k800i to resolve these issues:

1.) Synchronize using an USB Cable.
2.) Browse Memory Contents Using Bluetooth.
3.) Browse Memory Contents Using USB when in "Phone Mode" and not "File Transfer Mode"


I hope this guide will help some one some where. 

Thank you for reading

Best Regards,
Fotis.

---

### Post by Aetherius on 2006-11-16
well i just got a k800i yesterday, if its anything like my past experience of syncing phones with ubuntu over bluetooth then its a nightmare ](*,)

a lil howto wouldn't be too bad

---

### Post by fotakis on 2006-11-16
Hello dude,

If you can wait until monday i will have written it up!

Cheers

---

### Post by .tommie on 2006-11-18
A good, central how-to with some input from different users might be very interesting. Also the how-to might be helpful for setting up other Sony Ericsson devices, like the K750i. :D

---

### Post by Aetherius on 2006-11-18
got it sorted pretty good, multisync did it well for me... only when i have ALL the plugins installed tho, odd. Also got kmobiletools to take control of my phone, allowing me to send text messages and dial-out from the computer. Kmobiletools is very patchy over bluetooth tho.

[http://www.ubuntuforums.org/showthread.php?t=242932](http://www.ubuntuforums.org/showthread.php?t=242932)

Next I'm gonna try to configure bluemon to open up multisync and sync whenever my phone gets close to the comp.

wish me luck

---

### Post by Ago12 on 2006-11-20
Good luck, I'm waiting for news! ;)

---

### Post by fotakis on 2006-11-22
Hello all,

First of all my apologies for not getting it done. I would like to inform you that I had to go to the hospital on Saturday for an operation, nothing planned, nothing serious thank god. I have to rest for serveral days, and I will be back at my computer from next week.

Best Regards,

Fotis

---

### Post by Aetherius on 2006-11-22
don't worry my friend, glad to hear you're ok

get well soon

aeth

---

### Post by .tommie on 2006-11-26
Get well soon, fotakis.

---

### Post by fotakis on 2006-11-28
Updated first post

---

### Post by Ago12 on 2006-11-28
Yihaa!

I'm gonna test that after dinner :p

Thanks you very much!

Are you better now?

---

### Post by fotakis on 2006-11-29
Hello ago,

Yes I am cool now, from what the doctor says :-)

Please let me know if you have any problems, so I can update the howto!

Best Regards,
Fotis

---

### Post by Ago12 on 2006-11-29
I had too much work yesterday.

Hence, I have not been able to apply it. And just now, I am in an english lesson, so I don't wan't to abuse :p

Just one question: how can you make contacts backups before starting, if possible on Ubuntu? :p

Thanks btw, and I'm glad you're cool: you are :p

---

### Post by Ago12 on 2006-11-29
I had too much work yesterday.

Hence, I have not been able to apply it. And just now, I am in an english lesson, so I don't wan't to abuse :p

Just one question: how can you make contacts backups before starting, if possible on Ubuntu? :p

Thanks btw, and I'm glad you're cool: you are :p

---

### Post by tyr1973 on 2006-11-29
Hi!

I have a K610i, and I seem to be able to connect my phone to multisync/evolution.  But nothing happens on either the phone or in Evolution. Do you have to edit some settings in the phone, which I have missed?

I hope someone can enlighten me, even if the thread is really about the k800

cheers

---

### Post by fotakis on 2006-11-30
Hello tyr,

Do you mean you tested the connnection in the 'Options' dialog of multisynhc and it worked?

---

### Post by tyr1973 on 2006-11-30
Hi!

I followed all the instructions in the howto, and when testing the connection everything seemed allright.  But there is no synchronisation taking place.  That is why I thought that I might have to edit something in the phone itself.

cheers and thanks for the quick reply

---

### Post by fotakis on 2006-11-30
Actually before doing anything on your phone, you can tweak the options on the first pluging which is the "Ximian Evolution 2" plugin.

Also on the dialog after step "7" there are three checkboxes, make sure you have them checked.

Best Regards,
Fotis

---

### Post by HellRat on 2006-12-20
Hi!

Nice work with the how-to. Im afraid I couldnt make it work though.. =(
I dont think this is a reason, but; I cant apt-get bluetooth. All the other stuff worked tho. I have made file transfers from my phione to my pc before so I dont think this is a reason why it doesnt work.

My trouble begins at 13) when I do a test connection. It says it fails even tho it finds my phone and its address in the step before. I can make the phone ask when connection is made and in that case it failes right after I granted connection in my phone. Know what could do this?

I run dapper and my hcid.conf looks a bit different from yours (I added the passkey "1234"; - stuff myself after reading the howto, it wasnt there at all before.):


options {
	autoinit yes;
	security auto;
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/pinwrapper;

	# D-Bus PIN helper
	#dbus_pin_helper;

	passkey "1234";
}

# Default settings for HCI devices
device {

	name "%h-%d";

	class 0x3e0100;

	iscan enable; pscan enable;

	lm accept;

	lp rswitch,hold,sniff,park;

}

---

### Post by brujoand on 2007-01-01
but if u guys cant get this to work.. [www.zyb.com](www.zyb.com) is  greate help with synchronization ;) 

cheers

---

### Post by mooter on 2007-02-06
Thanks for the how to:  it works!
It really helped knowing about the conf file, then again, I'm learning those conf files are important to getting ones Linux to work right.

So, are there other programs good for phone syncing other than Evolution?
It's ok, I just don't need it as an email client, but that doesn't mean I have to use the email:)

---

### Post by usmjan on 2007-02-06
Thx for info..... Will the same process work on SE K510i.

---

### Post by HellRat on 2007-02-26
Hello!

I tried the howto again in edgy and still didnt get it to work out for me.. When I search for units, my phone shows in the dialog and I chose it. Though, when Im trying to connect with "test connection" it says "connection failed."

Anyone know what could cause this? 

Please.. =(

---

### Post by fotakis on 2007-02-26
Hello there,

If the scan shows your device, then a connection is there. I think you have to pair your pc and phone permanently for the "Test Connection" to work. 

I will read over the how-to just to remember a few things, but you might give my suggestion a try in the meanwhile.

---

### Post by gweaver on 2007-04-27
I'd like to be able to sync my phone (K510i) with Evolution too, but i can't be bothered with doing all the config myself.

I really hope the developers can put some effort into creating a seamless phone contacts sync utility or module for Evolution. Actually, I'd really like to be able to sync contacts with Thunderbird, like I can using MyPhoneExplorer under Windows.

---

### Post by [o_0] Rob on 2007-05-25
Hi all,

Thanks fotakis for your guide. I have a problem trying to connect to the k800i though and I hope someone's able to help :-)

When I click on "Test Connection" (step 13), the k800i prompts for a passcode. After entering this, a dialog box states, "Bluetooth connection failed. Check bluetooth settings on other device." I have double checked /etc/bluetooth/hcid.conf to make sure the passcode is indeed 1234 but the phone won't accept this. fotakis mentions in his initial post that he had to set a permanent pair between his computer and phone for it to work. Would someone be able to tell me how to do this? On the phone I have tried going to: Bluetooth > My devices > New device, but a dialog box says "No bluetooth devices found".

I suspect I missing something simple here. I switched from MS XP to Ubuntu less than a week ago so please excuse my ignorance.

---

### Post by fotakis on 2007-05-25
Hello rob,

From what I can remember the phone asked me if I wanted to pair it with the device asking for the connection.
Any time the pc bluetooth tries to contact your phone you get that question, to be honest I can't remember at exactly which step. 

If you can try the process again, then you should definitely reach that message. BTW- Start the pair from the computer instead of the phone.

Lastly, I hope you are running edgy because I haven't tested with feisty yet.

Best Regards,
Fotis

---

### Post by [o_0] Rob on 2007-06-05
Thanks fotis. I ended up solving the problem. Turns out it was the line, "security user;" in /etc/bluetooth/hcid.conf that was causing the problem. I changed "user" to "auto" as per your original post, restarted gnome and "Test Connection" then successfully paired the phone.

To HellRat:
it sounds like you have exactly the same problem. Double check you didn't made the same mistake as me.

---

### Post by gweaver on 2007-06-29
There is a poll on Mobile Device Synchronisation here:
[http://ubuntuforums.org/showthread.php?t=484251](http://ubuntuforums.org/showthread.php?t=484251)

You may want to vote and add comments.

---

### Post by fotakis on 2007-06-29
Cheers

---

### Post by forumreader on 2007-07-15
Okay, I've been working through this and been having my fair share of troubles.  I followed the steps laid out by fotakis (thanks) and everything was going well until I got to the "test connection" step (step 13).  I read through the thread and saw that rob had the same problem.  Unfortunately, his solution did not help me, I had already edited my hcid.conf and set the security to auto.  I have double checked every step that fotakis has laid out and am sure that everything is right were it should be.  BTW, I'm running Feisty.

Now, just so it's clear, what is happening is when I hit "test connection" in multisync, the computer attempts to communicate with my phone.  This starts well, but after I enter in the pin, 1234, the phone responds with "connection failed".  I checked and re-checked the pin number, even changed it in the hcid.conf to see if that might help.  To be completely thorough before bothering people here in the message board, I attempted to pair the phone with some different programs (set it up as a remote device, etc.) and every time I would get to the point where it wanted a pin before moving on, the connection would fail after I entered the key.  I even grabbed another bluetooth phone and attempted to pair it with the computer and was met with the same "connection failed" error after entering the pin.

I have been able to use bluetooth for other purposes on my computer, even with my k800i.  I frequently use bluetooth to transfer my pictures to the computer, works very well.  I just can't seem to get it to work with anything that wants a permanent bond between the 2 devices.  

I hope someone has something to offer, I have been working with this for the past few hours and am determined to make it work!  Thanks.

---

### Post by forumreader on 2007-07-15
Okay, here's my update.  It works!  The part that I missed was that I needed to initiate contact between my phone and computer from the phone side before I could move forward.  All that I had to do was go to bluetooth>My devices>New device and add my computer (on my phone).  When it asked for the pin on my phone I entered the pin from my hcid.conf and then moved on with step 13.  After I had made this "first contact" from my phone, when I tested the connection, there was no failure!

Thought it was worth letting everyone know, so if you get stuck in the same place I did it can maybe help you out.  Thanks again to everyone who has contributed in this thread.

---

### Post by fotakis on 2007-07-16
Thanks for the update,

When I tried it i had to set the permanent link the other way around, but at least is good to know you can try both ways

Thank you,
Fotis

---

### Post by codedmin on 2007-08-02
I still stuck in test connection :(

I'tm trying in htc tytn wm6 but no luck at all :(

---

### Post by codedmin on 2007-08-02
When i search i find my pda, but it only show the mac address without channel

00:12:D1:CD:F1:B6 - No IrMC synchronization

Anyone with same problem?

---

### Post by fotakis on 2007-08-03
codedmin,

I think you should take a look at [synce]("http://www.synce.org/index.php/SynCE-Wiki").

---

### Post by ryu kun on 2007-08-06
> **tyr1973 said:**
> Hi!

I followed all the instructions in the howto, and when testing the connection everything seemed allright.  But there is no synchronisation taking place.  That is why I thought that I might have to edit something in the phone itself.

cheers and thanks for the quick reply

I have the same problem with my k750i. I've changed the options of the first plugin but it didn't help.

I am trying kmobilephone utility now. It can see my phone contacts but can't import them to anywhere... I think it needs Kontact to do that.

---

### Post by maarten80 on 2007-08-11
I have a Z530i and the syncing works great. Thanks for the howto.

I'm having one small problem however. Entries that were already in the phone do not get synced to the empty Evolution calendar. New entries that I make in the phone get synced, same as new entries made in Evolution.

The log of multisync says however with the first coupling: 234 entries synchronized. So it does seem to sync the items, but they I can't see them in Evolution...

... weird?

---

### Post by zepto on 2007-08-12
Hi, 
I have the same problem, and I can not see entries from phone only those made in Evolution. Strange....

---

### Post by exz on 2007-09-04
Hi..

I seem to be having the same problem as zepto and maarten80. multisync says that it has successfully synchronized 361 entries but I cant find anything in evolution. Haven't tried adding new contacts to evolution and syncing back, but I suppose I'm stuck with the same problem.. Would be thankful if anyone had any suggestions.

Thanks

---

### Post by rodgana on 2007-12-11
Exellent, it works well for a sony ericsson Z550

---

### Post by fotakis on 2007-12-11
thanks

---

### Post by brainstuff on 2008-04-27
Just thought I'd check in to let anyone know who's looking to get inside their k800i that I've installed Wammu and gmobiletools from Synaptic, and I'm happily composing SMSes, backing up contacts, and browsing phone memory with these two tools! Connected via USB cable to my Thinkpad T21 running Xubuntu 8.04. There are options to do the same using irda (infra red port) and bluetooth. These are excellent tools as far as I can tell (only been using them for about half an hour mind you). Looks like between them they'll support a whole bunch of phones too. Happy phoning :)

---

