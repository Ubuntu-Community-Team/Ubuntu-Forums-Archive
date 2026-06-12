---
title: "Nvidia drivers will not download."
date: 2009-08-14
forum: New to Ubuntu
---

### Post by Jason Weiss on 2009-08-14
I have been having a lot of trouble installing my Nvidia drivers. 
I have tried the gui method through the systems menu but every time gnome does does not restart. 

So I tried to download and install the driver with command line, using this method. 
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Graphics_Card)

But it looks to me that the problem is that the driver does not download. 

Can anyone help me with this?

```
new@new-desktop:~$ wget -O NVIDIA-Linux-x86-pkg1.run http://www.nvidia.com/Download/index.aspx?lang=en-us
--2009-08-15 11:58:58--  http://www.nvidia.com/Download/index.aspx?lang=en-us
Resolving www.nvidia.com... 203.26.28.161, 203.26.28.155
Connecting to www.nvidia.com|203.26.28.161|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `NVIDIA-Linux-x86-pkg1.run'

    [      <=>                              ] 41,010      14.2K/s   in 2.8s    

2009-08-15 11:59:01 (14.2 KB/s) - `NVIDIA-Linux-x86-pkg1.run' saved [41010]

new@new-desktop:~$ sudo sh NVIDIA-Linux-x86-pkg1.run
: not foundx-x86-pkg1.run: 1: 
NVIDIA-Linux-x86-pkg1.run: 2: cannot open !DOCTYPE: No such file
NVIDIA-Linux-x86-pkg1.run: 2: html: not found
NVIDIA-Linux-x86-pkg1.run: 3: cannot open HTML: No such file
NVIDIA-Linux-x86-pkg1.run: 4: cannot open HEAD: No such file
NVIDIA-Linux-x86-pkg1.run: 5: cannot open title: No such file
NVIDIA-Linux-x86-pkg1.run: 5: -: not found
NVIDIA-Linux-x86-pkg1.run: 6: cannot open META: No such file
NVIDIA-Linux-x86-pkg1.run: 6: http-equiv=Content-Type: not found
NVIDIA-Linux-x86-pkg1.run: 7: cannot open meta: No such file
NVIDIA-Linux-x86-pkg1.run: 8: cannot open META: No such file
NVIDIA-Linux-x86-pkg1.run: 9: cannot open meta: No such file
NVIDIA-Linux-x86-pkg1.run: 10: cannot open meta: No such file
NVIDIA-Linux-x86-pkg1.run: 11: cannot open meta: No such file
NVIDIA-Linux-x86-pkg1.run: 12: cannot open meta: No such file
NVIDIA-Linux-x86-pkg1.run: 13: cannot open meta: No such file
NVIDIA-Linux-x86-pkg1.run: 14: cannot open link: No such file
NVIDIA-Linux-x86-pkg1.run: 15: Syntax error: redirection unexpected

```

---

### Post by starcraft.man on 2009-08-14
The link is incorrect, really... not even close. You need a direct link to the .run file not the site.

Go to [here]("http://www.nvidia.com/Download/index.aspx?lang=en-us") then put in information and find driver ya need. Scroll down to step 2 and copy the link to the .run and put it in substitution for the address in the guide (the wget line I mean). Alternatively you can just download the file from a GUI browser to your home directory and continue with instructions. I'd just give you the right link, but it depends on what card ya have and your distribution version (32 or 64).

I don't like the instructions, they aren't complete for a manual install. Please follow these instructions I just put on [pastebin]("http://pastebin.ca/1530070"). Ignore 7b completely (go right to 8 ) if you haven't ever installed nvidia drivers out before. I advise you print them out or write down the commands after you go to console. Ask questions before following it please if your confused, it's better explained though.

---

