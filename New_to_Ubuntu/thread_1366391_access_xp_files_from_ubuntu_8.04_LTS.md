---
title: "access xp files from ubuntu 8.04 LTS"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-12-28
Hi Ubuntu Community:

I am having difficulty accessing shares that exist on my xp machine from my ubuntu 8.04 LTS machine.

I realize that this issue is discussed often on the forums... but could not find anything to work.

Here is what I did:

1. Installed samba using instructions at [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba"). I followed the instructions on that page all the way down to the heading marked "Samba Client Manual Configuration." (Could there be a problem with passwords?)

2. Tried: places > network  and then clicked on icon: "Windows Network." Got the message: UNABLE TO MOUNT LOCATION.

3. Tried: places > connect to server .... and filled in the information on the pop-up window... please see the screenshot-1.png attachment. 

Screenshot attachment shows a gnome-RDP session to the xp machine I want to access files on... in clockwise order [LIST]
[*]the screeshot shows: explorer with the folder named "personal" listed as being shared (indicated w/ hand holding the "personal" folder icon.
[*]the properties of the "personal folder"
[*]system properties showing allowing remote desktop to the xp machine
[*]a command window showing the results of ipconfig... and the ip address of the xp machine, and
[*]results from using places > connect to server and filling in the info in the pop-up window.
[/LIST][ATTACH]141482[/ATTACH]

The attached file "screenshot-2.png" shows the pop-up window that results from the last itemized step, above. That pop-up wants a domain name and password! 

What would they be?

So, not knowing what they should be, I just click on "connect" and eventually get the pop-up message shown in the attachement "screenshot-3.png" that shows I can't connect to the location I want!

:-(

What am I doing wrong? Please help me connect to my xp machine to share files!

Many thanks!
Phil Smith
Duluth, GA

---

### Post by audiomick on 2009-12-28
Hallo.
I haven't done this exactly, so I don't want to make any wild guesses.
There is a thread here:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

which is really long, but contains useful info. Particular attention should be given to the links in dmizer's signature.

---

### Post by Old Jimma on 2009-12-28
Audiomick:

Thanks, Dude!

I'll give it a try and get back to you!

In the mean time... have a Happy New Year! Try to enjoy that German Beer. I know it isn't from Milwaukee, but give it a try, anyway!

All the best,
Phil

---

### Post by mapes12 on 2009-12-28
Hi Phil

I found Samba far too difficult to configure. I found a much easier way to access my windoze box from my Ubu box by using PyNeighbourhood. This is what worked for me:

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

BTW - if you're running Vista or whatever the above should still help you out but the screens in MS may be different. I don't know because MS are not getting any more money from me. XP is the MS end of line from now on..........

---

### Post by audiomick on 2009-12-28
> **mapes12 said:**
> Hi Phil

I found Samba far too difficult to configure. I found a much easier way to access my windoze box from my Ubu box by using PyNeighbourhood..

According to the description in Synaptic, this is a graphical interface for setting up SMB / samba shares, i.e. doing it the easy way. Might be a good tip..

It is spelled "pyNeighborhood" in synaptic.

---

### Post by Old Jimma on 2009-12-28
Hi All:

My many thanks to Audiomick and Mapes12 for their excellent suggestions!

I tried out **[COLOR="Red"]pyNeighborhood[/COLOR]**. It is very cool... and I think I am getting close to sharing files with the XP machine.

Here is where the hang-up may have been. Mapes12 suggested:

> Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

I did that and noticed that when I right clicked the globe and selected "scan" it showed that "WORKGROUP" appeared under the globe. On my XP machine, the workgroup names is "MSHOME"

Do I need to make some adjustment for this?? After right clicking on "WORKGROUP" I get the message: "failed to scan workgroup WORGROUP."

I have a sneaking suspicion that the workgroup name on the XP machine may need to be changed to WORKGROUP, right? If so, how do I do that?

Thanks for your continuing help!

Phil Smith
Duluth, GA

ps. Mapes... what is that 16oz can on your photo? Milwaukee, right?

---

### Post by audiomick on 2009-12-28
> **Phil Smith said:**
> Hi All:

I did that and noticed that when I right clicked the globe and selected "scan" it showed that "WORKGROUP" appeared under the globe. On my XP machine, the workgroup names is "MSHOME"


They have to be the same. Can't remember how to change it in XP, it's been too long...

I have seen a few posts that indicate that it works better to change the windows to "workgroup" than the ubuntu to "mshome", but I can't verify that.

---

### Post by Old Jimma on 2009-12-29
Hi Audiomick:

To change the workgroup name on XP:

start > right click my computer > computer name tab , then click on the "change" button to rename the computer or join a domain. That leads to instructions to change the workgroup.

I did this, and things still don't work.

Also, I tried [ttp://ubuntuforums.org/showthread.php?t=1169149]("ttp://ubuntuforums.org/showthread.php?t=1169149")

Those instructions enabled me to see my ubuntu file system... not my XP file system.

All the best,
Phil

---

