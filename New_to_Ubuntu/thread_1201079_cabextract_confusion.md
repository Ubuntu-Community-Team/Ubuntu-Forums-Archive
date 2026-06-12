---
title: "cabextract confusion"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by to25 on 2009-06-30
Hi i am completely new to linux and i am trying to install a wireless driver using ndiswrapper and the site i am following tell me to uninstall the driver with cabextract or unshield. I installed it but i can figue out how to use it. I see that it installed in synaptic but no where else. please see me as a complete noob to computers let alone linux. thanks

---

### Post by spcwingo on 2009-06-30
Cabextract is a terminal program.  Open a terminal (applications>accessories>terminal) and type:

```
cabextract -d /directory_to_extract_to/ /path_to_cabinet/
```

BTW, what card are you trying to get going?  To find out, just run this command:

```
lspci
```

if it's internal, or:

```
lsusb
```

if it's a USB card.  Either way let us know how it turns out, or if you need more help.

---

### Post by 3rdalbum on 2009-06-30
Like what spcwingo said, but I'll point out that you can drag folders and files to the terminal and it will automatically fill in their path.

So, you can type:

"cabextract -d "

and before pressing Enter, drag the destination folder to the terminal, and then drag the .cab file to the terminal. Click on the terminal to bring it to the front again, and press Enter.

---

### Post by to25 on 2009-06-30
Well I was going to start another thread if this didn't work but maybe you could help me out. I tried to follow alot of sites to install b43 or ndiswrapper but I may not be doing it right. I am working with:

gateway 7405gx
broadcom bcm4306 802.11b/g wireless lan controller (rev 03)
ubuntu (jaunty)

Now jaunty comes with b43 driver and i installed b43 fwcutter via the terminal, activated b43 driver, and then went and modprobe       "sudo modprobe b43"       but thats as far as I got because I could not find any other instuction and that did not work. tried several time but the only thing that happens is that the wireless icon lights up on my keyboard as if it is on but the wireless still doesn't work.

I have tried to use ndiswrapper and or ndisgtk. I installed via the terminal and then downloaded and extracted drivers from many different sources( not sure if the were reliable). The drivers were on my desktop, installed by windows wireless device and it says hardware not found.

now I am trying to install following the instructions at help.ubuntu.com the WifiDocsDriverNdiswrapper page 

Most site say generally the same thing so I am either missing something or very confused. Again I am really new to this, I literally started just a week ago with no prior knowlege of linux. So if you can help and need aditional info I would appreciate it.

---

### Post by to25 on 2009-06-30
i'm sorry and I know I might begin to frustrate you guys with my stupid questions but the site does not tell me where I sould extract to so I assume that I should just do it on the desk top butwhen I do that I get an error from that looks like

[/home/to/Desktop/sp28537.exe]
   End-of-central-directory signature not found. Either this file is not
   a zip file, or it constitutes one disk of a multiple-part archive. In the 
   latter case the central directory and zipfile comment will be found on
   the last disk(s) of this archive.
zipinfo:       cannopt find zipfile directory in one of /home/to/Desktop/sp28537.exe or
   /home/to/Desktop/sp28537.exe zip, and cannot find /home/to/Desktop/sp28537.exe period

What do I do?

---

### Post by to25 on 2009-07-01
ok guys thanks for the help, but some how i do not need it any more. Magically I tried the b43 way again and now it works.

After posting I decided to give it another shot, I do not remember if the b43 driver was activated but I suggest anyone who needs this try both on and off. 

I proceeded to install b43-fwcutter via the terminal. (i'm not sure if this turns on the b43 driver but it was on, which might help with statement above.)

I deactivate the b43 driver and then reactivated it.

I restarted my laptop and WAL LA.

I don't know what happened but those in need can try this out. It was stated on other site like ubuntucrates (I think thats the name). I just added the activate and deactivate parts. It probably was on other sites I did not see. 

Thanks again

---

