---
title: "Problem with RTL8191SEvB [10ec : 8172] card."
date: 2014-03-10
forum: Networking &amp; Wireless
---

### Post by work2 on 2014-03-10
Hi varunendra!

Followed your steps didn't work...

outputs:
# modprobe -rv rtl8192se
rmmod rtl8192se
rmmod rtl_pci
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211

# modprobe -v rtl8192se
insmod /lib/modules/3.11.0-18-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko 
insmod /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko 

... downloaded your link signature, the first execution of rtl8192sefw.bin got an error of permission...
Done chmod +x rtl8192sefw.bin and next got an error "impossible to execute binary file"...


Tryed:
#rfkill unblock all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Didn't  Work... Also installed xbindkeys, create an Hot Key and only change de  Soft blocked from "no" to "yes"... Hard blocked stays allways the same!


Infos:
# lspci -vvnn | grep RTL8191SEvB
14:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)

Could you give some help?
Best regards

---

### Post by varunendra on 2014-03-10
Welcome to the forums work2! :)

From your description, I can only see what you have tried, not what you tried it for??

Please explain in detail the kind of problem you were having, any relevant background info, system, OS, OS version etc. And how do you know you need those exact steps that you followed?

Wireless problems are very subjective - means the cause and the solution may differ from person to person, even if the symptoms are same.

Apart from your description, I'd also like to see the "wireless_script" report. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by bapoumba on 2014-03-10
Moved to its own thread. Please suggest an appropriate title :)

---

### Post by varunendra on 2014-03-10
> **bapoumba said:**
> Moved to its own thread. Please suggest an appropriate title :)

Thank you .... erm... ***who??*** :confused:
[COLOR="#696969"]*(impossible to decide who stole whose.. elfy stole the "id" bapoumba, or bapoumba stole avatar, comment, signature from elf.. :( ,so 'whoever you are'.. :confused: :confused: :confused: :confused:)*[/COLOR]

---

### Post by bapoumba on 2014-03-11
> **varunendra said:**
> Thank you .... erm... ***who??*** :confused:
[COLOR="#696969"]*(impossible to decide who stole whose.. elfy stole the "id" bapoumba, or bapoumba stole avatar, comment, signature from elf.. :( ,so 'whoever you are'.. :confused: :confused: :confused: :confused:)*[/COLOR]

You are very welcome, Varun :)

---

### Post by work2 on 2014-03-11
Hi again!
Thank´s varunendra for your reply and welcome.

I´ve followed the post [http://ubuntuforums.org/showthread.php?t=2182953](http://ubuntuforums.org/showthread.php?t=2182953), because i can´t turn on my wireless card RTL8191SEvB.
In the network connections info, got a message "wi-fi is desconnected by a physical switch", but i don´t have a physical switch, only FN+F8 hot keys in windows... used xbindkeys to create one Hot Key but only change the "Soft blocked" state from no to yes as previous mencioned.

About the "wireless_script":
...
HTTP request sent, awaiting response ... 200 OK
Size: 4210 (4,1K) [text/plain]
Last header changed is missing -- time stamps disabled.
--2014-03-11  18:27:01--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Reuse the existing connection with dl.dropboxusercontent.com: 80
HTTP request sent, awaiting response ... 200 OK
Size: 4210 (4,1K) [text/plain]
Saving in: "wireless_script"

100%[================================================>] 4.210 --.-K/s in 0s

2014-03-11 18:27:01 (167 MB/s) "wireless_script" saved [4210/4210]

Results saved in "wireless-info.txt".


I´ve installed Ubuntu 13.10 64bits and my laptop is a Toshiba Satellite L500-13w.


Best regards.

---

### Post by varunendra on 2014-03-11
> **work2 said:**
> 2014-03-11 18:27:01 (167 MB/s) "wireless_script" saved [4210/4210]

**Results saved in [COLOR="#0000CD"]"wireless-info.txt".[/COLOR]**
I need to see the contents of that file (wireless-info.txt). Please find it in your Home directory, and either upload its contents or attach the file itself in your next post here.

---

### Post by work2 on 2014-03-12
Varun, here´s the contents of "wireless-info.txt" in attach!

---

### Post by varunendra on 2014-03-12
I don't see anything wrong with the firmware. Please check your laptop's user manual to see if there is a physical switch somewhere that needs to be turned "On". For example, some Lenovo models have a tiny switch (apart from the Fn+ key combo) in their side that users very often seem to miss.

If it has no such switch, or is turned "On", please check your BIOS to make sure wireless is enabled from there. _If it is NOT a UEFI based installation_, also try resetting the BIOS if everything else seems to be okay. Of course toggle/double-check the physical switch (if any) and the Fn+key combo (or whatever you have to toggle the wifi on/off) after resetting the BIOS.

Also, some BIOS have a setting to automatically turn the wireless card off if a wired connection is detected. So also check if your BIOS have such a setting, and turn it off if there is. Additionally, unplug the cable > reboot and check "rfkill list" output to see if the hardblock is still there. _Preferably, do all the tests without the cable plugged in_.

If none of these help, and you are sure the hardware switches are okay, please reboot and post back the full outputs of -
```
lsmod
egrep 'wlan|rtl81|phy' /var/log/syslog
```

---

### Post by work2 on 2014-03-13
No physical switch in this model, only HOT KEY, and checked user manual to confirm. (The user Manual is only for Windows :evil:, even screens...)

**User Manual:**
[http://www.manualslib.com/manual/180193/Toshiba-Satellite-L500.html](http://www.manualslib.com/manual/180193/Toshiba-Satellite-L500.html)

Sory, the Ubuntu 13.10 version is 32bits not 64bits, Toshiba Satellite L500-13w.
Checked BIOS, option "Wireless Comm SW: [ON]". Changed to [OFF], same results!
Is not a UEFI based installation. Reset bios by Restore Default Settings, then cheked status "Wireless Comm SW" was ON, same results!!

Done rfkill list
[I]0: phy0: Wireless LAN
           soft blocked: no
           Hard bloked: yes[/I]

Nothing works, swicthes ok, no wired connection, reboot and here´s the outputs without the cable plugged in:

lsmod results:
[ATTACH]251095[/ATTACH]

Had to zip egrep results:
[ATTACH]251094[/ATTACH]


](*,)

---

### Post by varunendra on 2014-03-14
I'm not even sure if I'm working in the right direction, but please show me some more information as requested below -

Please reboot, and as soon as the system is ready, run this code to copy syslog messages from only current session onto your desktop -
```
tac /var/log/syslog | sed '/ kernel: .* 0.000000/ q | tac > Desktop/syslog.txt
```

This will create a file "syslog.txt" on your Desktop. Attach this file here in your next post.

Along with the above file, please also post back the outputs of -
```
cat /proc/bus/input/devices
grep [[:graph:]] "/sys/devices/pci0000:00/0000:00:1c.3/0000:14:00.0/ieee80211/phy0/rfkill0/"*
```

---

### Post by work2 on 2014-03-17
Hello again Varun!

Finally got the wireless card on! :D
First done more updates to the OS and next, one more time in BIOS, done "Restore default settings" and confirm option  "Wireless Comm SW: [ON]".
Didn´t work but after enter again in BIOS, restore and aplly again got:

#rfkill list
0:   phy0: Wireless LAN
      Soft bloked: no
      Hard bloked: no

Probably after running your wirelless script, and follow your tips, the  problem should be solved, but by some reason my BIOS wasn´t applying  correctly the changes... :confused:


Varun, thank you very much for your help, 
You´re the man =d>!!
Best regards!!

---

### Post by varunendra on 2014-03-17
I'm not sure what I did, but glad it's working now :p

Perhaps I should add one more point to my 'BIOS reset' suggestions since now - that one should also try to drain 'All Power' from laptop *(disconnecting AC adapter, battery, push power button a few time to make sure all power is drained etc.)* if a BIOS reset and all other tricks don't seem to work with a 'Hard-block' problem. :-k

Remnant power not letting the card/firmware to properly reset is the only reason I can think of why it didn't work previously, while magically did on next attempts.

Anyway, Thank You for the feedback with description of what made it work - definitely helpful to many. Please mark the thread as **[SOLVED]** now to make it more useful. :)

---

### Post by work2 on 2014-03-19
Yes, drainning all power from devices somethimes it´s the secure way to prevent stupid erros to occur!
Working on desktops, just by unplugging the power cord, take out the CMOS battery and whait 20 seconds for discharge the capacitors was enought to somethimes resolve directly some POST errors, BLUE SCREENS and errors loading the OS...

The problem is that somethimes we find laptops where CMOS battery it´s very hidden and it´s necessary to disassemble them totally...
In other cases the CMOS battery is welded in the motherbord... :(

Thread marked as solved! 

Thank´s Varun :)

---

