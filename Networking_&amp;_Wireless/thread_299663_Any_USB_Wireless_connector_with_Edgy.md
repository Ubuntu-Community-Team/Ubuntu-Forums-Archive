---
title: "Any USB Wireless connector with Edgy?"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by BartlebyScrivener on 2006-11-14
So, given my own experiences and the litany of failures abundantly documented in this forum, can anyone advise of a wireless 802.11 g USB connector that works "out of the box" with Edgy?

I've seen the table listing those that supposedly do, and also seen the same models listed here as being broken by those who upgraded from Dapper to Edgy.

If anybody can report that they plugged one in and it worked, please do. I can still take my Linksys back at Compusa and swap for one that works, if there is such a thing.

Next question, will there be a fix of the wireless problems, or must we wait for Feisty Fawn or roll back to Dapper Drake?

Thanks,

rd

---

### Post by kishd on 2006-11-14
I have a netgear w111gt usb wifi adaptor. Did not work out of the box but after compiling and installing the latest ndiswrapper and loading the modules it has been rock solid even after a suspend and resume on my laptop.

---

### Post by BartlebyScrivener on 2006-11-14
Thanks for the help.

The one I saw at CompUSA was a Netgear WG111, which others seem to have installed using ndiswrapper. Could you check the model number. I'd really like to get this machine running, and don't want to run CAT5 cable to do it.

Thx

rd

---

### Post by FrodoB on 2006-11-14
Two very stable USB Wireless devices, both require building the drivers. The 
Belkin F5D7050 ver 4000  is typically available at local retailers in the US.

Belkin F5D7050 ver 4000 ZyDas Native Driver Instructions:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

Belkin F5D7050 ver 3000 Ralink rt73 Instructions:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by BartlebyScrivener on 2006-11-14
>> Belkin F5D7050 ver 3000 Ralink rt73 Instructions:
https://help.ubuntu.com/community/Wi...cs%2FDevice%29<<

Wow, thanks for this one. I'm going to try it on my Linksys WUSB54GC - it uses the same same Ralink drivers, but the instructions I was going from were nothing so thorough as those. 

Thanks again,

rd

---

### Post by FrodoB on 2006-11-14
Keep me informed. I have applied these instructions to Ubuntu, Slackware, and Debian with good success and I want to make sure that they are clear for everyone. The Belkin works really well, just plugs and plays once configured. No freezes on unplugging either.

---

### Post by BartlebyScrivener on 2006-11-19
FrodoB,

Those instructions did it! 

Worked like a charm installing the Ralink drivers for the Linsys WUSB54GC.

I used several other misguided instructions before, which did not include the fromdos conversion or blacklisting the original driver.

Thanks so much. There were one or two tiny nits in the instructions, such as a couple missing sudo commands, especially when editing the rtmp_def.h but otherwise the instructions were clear, simple, and accurate. 

I suggest anybody that needs Ralink drivers should use them. I combed the boards searching on my device name, when I should have been looking for "Ralink" 

Thanks again,

rd

---

### Post by FrodoB on 2006-11-19
Thanks for the feedback. I think that the sudo issue with editing the rtmp_def.h file must have been caused by the "sudo fromdos *" issued just before this? Afterall we did make everthing read write with chmod just two steps before. What do you think it is? 

I guess I need to put a reinstall from scratch on my list of projects to debug these nits that are in there.

---

### Post by BartlebyScrivener on 2006-11-19
>> fromdos

I'm still so new that I don't know what caused it, but I was unable to save changes in rtmp_def.h until I used sudo gedit.  

Speaking of fromdos, for clarity's sake, the path here should be to the Module directory?:

>> Change all of the files to the UNIX text type:

>> user@ubuntu:~$ fromdos * 


>> I guess I need to put a reinstall from scratch
>> on my list of projects to debug these nits

I really don't think that's necessary. It's a model of clarity and completeness compared to the other sets of directions I struggled with before finding it. Besides about the time you got around to reinstalling from scrath, Ralink would come out with new drivers or the Ubuntites would issue a fix.

Anyway, thanks again.

rd

---

### Post by FrodoB on 2006-11-19
You need to run "fromdos *" in the directory where you want all of the text files to be of UNIX type.

---

