---
title: "Problems setting up certain parts of Jaunty"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by ketedford on 2009-07-19
Hello All --
I am about 1 week in to now using Ubuntu 9.04 with all current updates. Wiped out Windows and hope to never look back. I have a few issues that I can not figure out and looking for some guru to help me out.
I have a Toshiba A135-S4656.

1) I can not get my SD Reader to work. Nothing happens at all when I insert media. As other people have done, I have run the**  lshal | grep SD** and get:

  info.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  pci.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  info.product = 'MMC/SD Host Adapter'  (string)
  info.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)
  pci.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)
eric@eric-laptop:~$ 

2) I am unable to run DVD movies. When I insert a DVD Movie, I get **AN ERROR OCCURRED Could not open location; you might not have permission to open the file.**

3) I have a Snap Server 220 and can access it with **smb://192.168.1.101/** but can not access it when I attempt to **CONNECT TO SERVER**

I am sure that these are pretty straight forward. However, being new, I am clueless. Any help would be appreciated.

---

### Post by halitech on 2009-07-19
1. not sure on the card reader so will leave that for someone else

2. did  you install ubuntu-restricted-extras and libdvdcss2?

3. not totally sure but are  you using windows share as the connect type or what on connect to server?

---

### Post by ketedford on 2009-07-19
> **halitech said:**
> 1. not sure on the card reader so will leave that for someone else

2. did  you install ubuntu-restricted-extras and libdvdcss2?

3. not totally sure but are  you using windows share as the connect type or what on connect to server?


For numbers 2 and 3, how would I figure that out? With Samba, I attempted to connect as Windows Share. 
Thanks for such a quick response.

---

### Post by halitech on 2009-07-19
2. open a terminal and type
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```it will ask for your password, type it in (you won't see what you are typing, this is normal)

3. when you go Places - Connect to server, there should be a few different options in a drop down at the top, which option are you selecting and then what are you putting in as the server?

---

### Post by ketedford on 2009-07-19
> **halitech said:**
> 2. open a terminal and type
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```it will ask for your password, type it in (you won't see what you are typing, this is normal)

3. when you go Places - Connect to server, there should be a few different options in a drop down at the top, which option are you selecting and then what are you putting in as the server?


Alrighty...thank you for getting the DVD to work. I really appreciate it!

When I Connect To Server, I choose WINDOWS SHARE and then for the Server, I put 192.168.1.101

Clicking to connect, I get **Cannot display location "smb://192.168.1.101/"** **No application is registered as handling this file**

---

### Post by ketedford on 2009-07-19
Hello All - still looking for any support for issues 1 and 3

---

### Post by halitech on 2009-07-19
have you install samba?

another option, if you can type in the address in the address bar in Nautilus and have it connect, you could simply bookmark it to add it to the left sidebar.

---

### Post by ketedford on 2009-07-19
Samba is installed. When I type it in to Nautilus I get:
[B]Could not display "192.168.1.101".
Nautilus cannot handle this kind of locations.
[/B]
Anybody know?

---

### Post by ugm6hr on 2009-07-19
> **ketedford said:**
> 3) I have a Snap Server 220 and can access it with **smb://192.168.1.101/** but can not access it when I attempt to **CONNECT TO SERVER**

I'm a bit unclear... Can you connect by en entering the location in Nautilus as above?

If yes, then I'd suggest you just add that as a bookmark in the bottom-left Nautilus pane.

The Connect to Server should work, provided you have the correct Workgroup name, but it is still easier to just use the fixed IP.

---

### Post by ketedford on 2009-07-19
OK, yes, it will work putting **smb://192.168.1.101/ **in Nautilus. I guess that solves the problem. Now, I just need help with the one other issue:

1) I can not get my SD Reader to work. Nothing happens at all when I insert media. As other people have done, I have run the**  lshal | grep SD** and get:

  info.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  pci.product = 'PCIxx12 SDA Standard Compliant SD Host Controller'  (string)
  info.product = 'MMC/SD Host Adapter'  (string)
  info.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)
  pci.product = '5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)'  (string)
eric@eric-laptop:~$

---

### Post by cariboo on 2009-07-19
Open a terminal and type:

```
dmesg | tail -n20
```

just after you have inserted a sd card into the reader. Paste the output in your next post.

---

### Post by ketedford on 2009-07-19
Here is what I get:

eric@eric-laptop:~$ dmesg | tail -n20
[109656.185122] [drm:i915_getparam] *ERROR* Unknown parameter 6
[110256.187879] [drm:i915_getparam] *ERROR* Unknown parameter 6
[112595.141191] [drm:i915_getparam] *ERROR* Unknown parameter 6
[112595.610604] [drm:i915_getparam] *ERROR* Unknown parameter 6
[113195.417579] [drm:i915_getparam] *ERROR* Unknown parameter 6
[113795.276925] [drm:i915_getparam] *ERROR* Unknown parameter 6
[114395.300377] [drm:i915_getparam] *ERROR* Unknown parameter 6
[116111.747622] [drm:i915_getparam] *ERROR* Unknown parameter 6
[116112.031367] [drm:i915_getparam] *ERROR* Unknown parameter 6
[116711.813641] [drm:i915_getparam] *ERROR* Unknown parameter 6
[117311.833547] [drm:i915_getparam] *ERROR* Unknown parameter 6
[117911.818486] [drm:i915_getparam] *ERROR* Unknown parameter 6
[119006.567658] [drm:i915_getparam] *ERROR* Unknown parameter 6
[119006.889900] [drm:i915_getparam] *ERROR* Unknown parameter 6
[119606.634921] [drm:i915_getparam] *ERROR* Unknown parameter 6
[120206.654191] [drm:i915_getparam] *ERROR* Unknown parameter 6
[120806.638392] [drm:i915_getparam] *ERROR* Unknown parameter 6
[126168.100028] tifm_core: MemoryStick card detected in socket 0:0
[126199.910759] tifm0 : demand removing card from socket 0:0
[126220.652030] tifm_core: MemoryStick card detected in socket 0:0
eric@eric-laptop:~$ 
eric@eric-laptop:~$

---

### Post by ketedford on 2009-07-20
Bump Up: Still need help with card reader. Please help!

;-)

---

