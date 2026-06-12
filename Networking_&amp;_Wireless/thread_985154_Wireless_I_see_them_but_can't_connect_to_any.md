---
title: "Wireless: I see them but can't connect to any"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by E-Cecilia on 2008-11-17
[I]I'm using Ubuntu Gutsy (7.10). I tried to upgrade to 8.04 twice but it wiped off my wireless connections completely.

I have a Broadcom wcard and, as a matter of fact, I have installed the restricted drivers for it right after the Ubuntu installation and it *seemed* like it was all set to go. Although right clicking on the Network Connection icon does show all the possible connections and their strenght, connecting to any is impossible.

Pleease, could you someone lend me a hand?[/I]

---

### Post by Olivier2371 on 2008-11-17
Hi there,

left clicking on the network icon shows you the networks available, not right clicking.

I have a broadcom 43. After installing unbuntu 8.04(not an update), I just went to the restricted drivers and found two wireless drivers available. One was STA the other was Broadcom 43 wireless adapter. That's it.(choose the broadcom 43 wireless driver)

When you click left on the network icon, can you select your network. If so
how do you connect.(eg.WEP or WPA automatic or WPA tkip).

---

### Post by Waderider on 2008-11-20
I'm having this same issue with a Broadcom BCM4303 card in a Presario R3000 laptop. I can see my network, put in the security and get as far as trying to obtain an address from my router.

If I find an answer I'll come back and post it.

---

### Post by Olivier2371 on 2008-11-22
What is the driver you are using in System->Administration->Hardware Drivers?

---

### Post by Joe2Shoe on 2008-11-22
E, update the repositories.

You must enable all the repositories to be able to download the needed drivers for your system:

Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

Good luck,
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', even though you have strong signal strength, it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

---

### Post by Olivier2371 on 2008-11-22
Here is the link that will explain a lot about B43.

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

I hope it is helpful.

---

### Post by E-Cecilia on 2008-11-25
> **Joe2Shoe said:**
> Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', even though you have strong signal strength, it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.


:( That sounds alright, but I don't have the Windows drivers with me... Can I get them somewhere on the internet or something?

---

