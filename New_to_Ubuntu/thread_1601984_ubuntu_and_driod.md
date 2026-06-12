---
title: "ubuntu and driod"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by mrtsmith on 2010-10-20
Hi all, i didn't see this answered in the beginner thread. So I will post . Being a newbie I have two big questions regarding my setup right now , Ubuntu 10.04

1st. Living in the US I was going to sign up for Ubuntu one but it's based out of england. Would I have any problems using that, legal or otherwise.

2nd. I have the iPhone right now. roughly like it but would prefer to use android if these qualification can be met.
    A). Does android sync to Ubuntu the same way the iPhone sync's with iTunes.
    B). Do android phones come with IR sensor ( like iPhone where you put the phone to your head to talk and the screen goes blank so you don't accidentally hit a button? Does the android come with the gyro-setup where you can move the iPhone and the sensors follow? Is there a compass like the 3GS and GPS on the Android. Does the android work with rhythmbox and evolution email

I would appreciate any feedback, I would once again prefer to go to android, and Ubuntu one but lacking the knowledge I prefer to be safe 

Thanks in advance.

---

### Post by Zzl1xndd on 2010-10-20
I use Ubuntu one in Canada and Haven't had any issues.

With Android I am going based on my phone the Acer Liquid E.

It does have a proximity censor. My phone does not have a Gyro scope but does have accelerometers, like earlier iPhones previous to the iphone 4. 

It has Google Maps and Navigation, And Navigation shows a compass and it has a GPS. I used drag and drop with all my music, not sure if it will work with Rythmbox, and its hooked up with my gmail account. I have Evolution also synced with gmail and google calender and it all works well together.

---

### Post by elliotn on 2010-10-20
I have a rooted HTC hero and it sync well with ubuntu, liga of staff worc, haven't had any issues

---

### Post by cariboo on 2010-10-21
> 1st. Living in the US I was going to sign up for Ubuntu one but it's based out of england. Would I have any problems using that, legal or otherwise.

Ubuntuone is hosted on Amazon's ECS servers. Which I believe is still an american company.

---

### Post by mrtsmith on 2011-03-07
Thanks for the reply's from everyone. It took me awhile to find where my posts where in the search.

---

### Post by 3rdalbum on 2011-03-07
I know this is an old thread, but you don't really "sync" your Android phone with Ubuntu using anything like iTunes.

The phone itself automatically syncs to Google's servers; if you ever lose your phone and buy another Android phone, you just put in the same username and you'll have all your data back onto the new phone. Pretty cool. Also avoids the need for bloated software like iTunes.

When you plug your phone into the computer, it appears as a "USB mass storage" device; like a pen drive. You can browse and modify the contents of the internal SD card, so you can add music and look at photos and stuff on your computer as though you were browsing a camera card.

---

### Post by willemferguson on 2011-03-16
Android 2.1 does not have full functionality for the phone acting as a modem. Android 2.2 has better provision for such services. PdaNet is a candidate, but which uses a Microsoft-oriented protocol. For Ubuntu users, EasyTether is a possibility. Find it on the Android Market. Since launching this software requires two terminal windows I use the following script to launch EasyTether from an icon on the desktop. My phone is a Motolola Milestone (i.e. Droid). 

#!/bin/bash

sudo whoami                # Obtain password from Ubuntu at start, not at end of script
                          #    when it can create problems when executing sudo to set up DHCP
# N.B: function declaration:
upper() { echo  $1 | tr 'a-z' 'A-Z'; }   # Convert $1 to uppercase

echo 
echo "Android 2.1 EasyTether Setup:"
echo "============================="
echo "1) Ensure USB cable is connected to Android phone."
echo "2) Ensure Android: USB_Connection > Memory_Card_Access is ON."
echo "3) Ensure Android: Settings > Applications > Development > USB_debugging is ON"
echo "4) Activate EasyTether on the Android phone"
echo 
echo "Fallback: easytether connect"
echo "          sudo dhclient easytether0"
echo 
echo "Continue (y/n) \c" 
response=""                           # Initialise response
answer=""                              # Initialise answer
read response                                                     # Get response to above question from keyboard
answer=`upper $response | grep Y`       # Convert to uppercase and find out if it contains a Y character
if $answer                                                            # answer = Empty if no Y character in the response, else not..
   then 
    echo "You chose to abort EasyTether Setup"        # If it does not contain a Y character
    echo                                                                                             #     Close down this script
    exit
   else                                                                                              # If it does contain a Y character
    xterm -rv -e easytether connect &                             #     Set up the driver
    sleep 3                                                                                        #     Wait 3 seconds for driver setup to complete
    sudo dhclient easytether0                                             #     Set up DHCP client
fi

---

### Post by seawolf167 on 2011-03-16
I have a Droid X for my personal use, and an HTC Evo 4G for work use. Both phones can do all the items you have listed above, except that when I sync I just have the phone mounted as external storage, then simply copy the files/folders (CLI or GUI) onto the mounted device (much easier IMO)

---

