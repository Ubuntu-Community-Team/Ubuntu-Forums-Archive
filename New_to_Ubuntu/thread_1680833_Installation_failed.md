---
title: "Installation failed"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by RolandSa on 2011-02-03
Hi,
based on a recommendation of a friend I tried to install Ubuntu. I burned the iso disk. It starts. The background is there, the mouse and the window with the choice of installation or trying Ubuntu comes up. When I chose to try Ubuntu the screen goes black. The mouse is still there but all stops. Nothing happens anymore.
I tried to install Ubuntu alongside of Windows 7 on my notebook. But when I start Ubuntu I get the same screen. It does not start.
What can I do?
Regards

---

### Post by Rubi1200 on 2011-02-03
Hi and welcome to the forums :-)

How much RAM do you have and what graphics card is installed?

Second, do you already have 4 primary partitions on the drive?

If yes, you cannot install until you create space; meaning 3 primary and one extended (with as many logical partitions as you want/it can hold).

---

### Post by RolandSa on 2011-02-03
Hi,
I use a notebook Acer Aspire 8530G. It has 4 GB DDR2 RAM. After my attampt to install Ubuntu alongside of Windows 7 I have the following partitions:
PQService - FAT32 - Primary (preinstalled by Acer)
C:Acer - NTFS - Primary (Windows 7 partition)
* - Other - Logical (Windows partition wizard does not know Ext4, this is the Ubuntu partition)
* - Linux Swap - Logical
* - NTFS - Primary (Rest of former partition D, created for installing Ubuntu)
Regards

---

### Post by RolandSa on 2011-02-03
Hi,
I forgott the graphics card:
ATI Mobility Radeon HD 4500 Series
ATI Radoen HD 3200 Grapgics
Regards

---

### Post by Rubi1200 on 2011-02-03
Hi,
please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by RolandSa on 2011-02-03
Hi,
I guess there is a misunderstanding. When I boot using the Ubuntu Live CD I get the choice of "Try Ubuntu" or "Installation of Ubuntu". If I choose "Try Ubuntu" the desktop disappears. I get a black desktop. Only the mouse is working there - nothing else. I cannot do anything.
Regards

---

### Post by Rubi1200 on 2011-02-03
Yes, misunderstandings...

In other words, you do not have Ubuntu installed because you are unable to even try it due to the black screen issue correct?

If that is the case, let's try something like this:
[https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=menuf6.1.png](https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=menuf6.1.png)

After the CD starts and you select language, try without changes etc, press F6 immediately to see the screen above.

There should also be an option called nomodeset; choose it and then Enter to continue.

Let me know if that helps.
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]file:///tmp/moz-screenshot-2.png[/IMG][IMG]file:///tmp/moz-screenshot-3.png[/IMG]

---

### Post by verymadpip on 2011-02-03
Hi RolandSA.

Is the .iso you've downloaded okay?  Check the MD5 sum to be sure.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  (I use something called Marxio when checking MD5s in Windows).

If that's good you can check if the CD has any defects at the options screen where you can choose 'try Ubuntu' 'install' etc.

Good luck

---

### Post by RolandSa on 2011-02-10
Hi,
I am sorry. I was away for one week.
The iso is OK. I used another iso disk that was OK and the installation was fine too.

I tried to press F6. But there appeared no such option like nomodeset when I start from the CD.

I alreasy have installed Ubuntu. And when I started it today it went up until the Look-in screen appeared. But I don't think that I already choose any passwords. So I tried passwords I usually use but nothing. Is there any way to go around this look-in screen? Perhaps Ubuntu will start now.

Regards Roland

---

### Post by RolandSa on 2011-02-17
Hi Rubi1200,
	 	 I use a notebook Acer Aspire 8530G. It has 4 GB DDR2 RAM. The hard drive has the following partitions:  
 *:PQService - FAT32 - Primary (preinstalled by Acer)
C:Acer - NTFS - Primary (Windows 7 partition)
 D:Data - NTFS - Logical
*: - Other - Logical (Windows partition wizard does not know Ext4, this is the Ubuntu partition)
*: - Linux Swap - Logical
*: - NTFS - Primary (Rest of former partition D, created for installing Ubuntu),
And this is the Graphics Card:
  
 ATI Mobility Radeon HD 4500 Series
ATI Radoen HD 3200 Grapgics 

I hope you have a good idea.
Regards Roland

---

### Post by Rubi1200 on 2011-02-17
Thanks for posting the information.

Here is what you can try.

When the computer starts and you see the entry for Ubuntu highlighted press "e" to edit.

Find the line that ends with quiet splash using the arrow keys to navigate.

After quiet splash add nomodeset so it looks like this > quiet splash nomodeset

Then "Ctrl" + "x" to boot.

Tell me if this makes a difference.

The other possibility is that this is caused by having Compiz enabled.

See here for more information:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials)

---

### Post by RolandSa on 2011-02-17
Hi Rubi1200,

[B]Thank you very much - it works!
[/B]
After restart Ubuntu asked for the download and installation of an FGLRX driver. I did so. Do I still need the "nomodeset" after "quiet splash"?

All the best,
Roland

---

### Post by Rubi1200 on 2011-02-17
> **RolandSa said:**
> Hi Rubi1200,

[B]Thank you very much - it works!
[/B]
After restart Ubuntu asked for the download and installation of an FGLRX driver. I did so. Do I still need the "nomodeset" after "quiet splash"?

All the best,
Roland
Excellent! I am really pleased this has worked out for you :-)

No, everything should be okay now. But, if not, you know what to do and we can make it permanent if needs be.

You can mark this thread Solved using the Thread Tools near the top of the page once you have checked that you don't need nomodeset again.

Enjoy!

---

