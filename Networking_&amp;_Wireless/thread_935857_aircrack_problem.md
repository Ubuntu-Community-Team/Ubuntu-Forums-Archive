---
title: "aircrack problem"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by master2010 on 2008-10-02
hi everyone, I have used aircrack-ng and aircrack-ptw to crack my wireless wep key. The wireless password is 128bit & I have captured 2,500,000 IVs but still I can not crack the password. I don't know why. When using aircrack-ptw, it gave me( allocating a new table key index = 0 then write my bssid then nothing happens.

---

### Post by alasarr on 2008-10-02
use the parameter z to decrypt in aircrack

---

### Post by master2010 on 2008-10-02
sudo aircrack-ng -z /home/mina/1987-01.cap . is it like this?


I got the same answer
Opening /home/mina/1987-01.cap
Attack will be restarted every 5000 captured ivs.
Starting PTW attack with 2541998 ivs.


                                 Aircrack-ng 1.0 beta1


                 [00:00:33] Tested 130561 keys (got 2541998 IVs)

   KB    depth   byte(vote)
    0  255/256   8E(2487040) A7(2565888) E0(2565632) 36(2565376) 7C(2564864) 
    1  254/  1   8B(2489344) FA(36864) ) F7(2601472) 4F(2596352) 1F(2593792) 
    2    0/  2   F7(7521024) 22(2608128) 4B(2596864) 1B(2595072) F3(2595072) 
    3    0/ 40   F2(9974016) 1D(2605568) 46(2594560) 16(2593280) 19(2588928) 
    4    0/  1   EC(12395008) 17(2606848) F1(2597888) 10(2594048) 40(2593024) 

Failed. Next try with 2545000 IVs.

---

### Post by binbash on 2008-10-02
try this please.back up the .cap

Convert it :

ivstools --convert asdasd.cap bsd.ivs
and crack it with aircrack-ng(not aircrack-ptw)

---

### Post by master2010 on 2008-10-02
same result 
 [00:00:32] Tested 130561 keys (got 2542031 IVs)

   KB    depth   byte(vote)
    0  255/256   8E(2487148) 4D(2533408) 74(2532908) B3(2532316) 57(2532284) 
    1  254/  1   8B(2489200) FA(38628) ) F7(2600716) 4F(2595956) 1F(2593540) 
    2    0/  2   F7(7517748) 22(2608524) 4B(2596216) 1B(2595072) F3(2594964) 
    3    0/ 40   F2(9969300) 1D(2605856) 46(2594452) 16(2592560) 19(2588892) 
    4    0/  1   EC(12389032) 17(2606920) F1(2597996) 10(2593796) 40(2592484) 

Failed. Next try with 2545000 IVs.


the password I want to crack is fedcba9876543210fedcba9876

is this difficult to be cracked

---

### Post by master2010 on 2008-10-02
does anyone know the solution to this problem?

---

### Post by binbash on 2008-10-02
Hmm it is 128 i missed that part.

you will need around 1500000 IVs for aircrack-ng and 80000Ivs for PTW according to aircrack-ng official site.

I have never tried to crack a password which is so long just like you.The only option you get is capturing more IVs.

Also you can open it via wireshark and inspect the packages if you are doing right

---

### Post by Papa-san on 2008-10-02
My son used something called 'Back Track 3' to show me he could crack my WEP encryption, and he succeeded to do it in less than 6 minutes. I believe it is a distro and he ran it as a live cd. (Needless to say I am running WPA now...)I don't need to worry so much about it now.

If you can download the .iso, you could use it. There is a good 'How To' on their site. 

Why do you need to crack your own router, though? If you press and hold the reset button, it will re-set everything to factory defaults...

---

### Post by binbash on 2008-10-02
> **Papa-san said:**
> My son used something called 'Back Track 3' to show me he could crack my WEP encryption, and he succeeded to do it in less than 6 minutes. I believe it is a distro and he ran it as a live cd. (Needless to say I am running WPA now...)I don't need to worry so much about it now.

If you can download the .iso, you could use it. There is a good 'How To' on their site. 

Why do you need to crack your own router, though? If you press and hold the reset button, it will re-set everything to factory defaults...

It does not matter since both are using same softwares, and patching the injected drivers done.

BUT i strongly suggest to visit their tho :

[http://forums.remote-exploit.org/](http://forums.remote-exploit.org/)

---

### Post by master2010 on 2008-10-02
thanks for replying, i am hacking my own router just for fun,to know if i am doing right.


also i tried this live cd, and i have many problems, first is to stop acpi and i succeeded to change this in the live cd, second my wireless driver is not supported and to install the driver, I have first to disable hal then restart, and because it is a live cd, nothing is saved

---

### Post by WitchCraft on 2008-10-02
> **master2010 said:**
> 
sudo aircrack-ng -z /home/mina/1987-01.cap


No, you forgot to specify the MAC address of the access point you want to hack:
```

 aircrack-ng -z -b 00:14:6C:7E:40:80 output*.cap

```
Where:

    * -z invokes the PTW WEP-cracking method.
    * -b 00:14:6C:7E:40:80 selects the one access point YOU are interested in.

**BTW: Is it a WEP key or is it actually a WPA key?**

If it's WPA, you need to install JTR, and pipe it into aircrack to use a brute-force attack.

---

### Post by master2010 on 2008-10-02
It's a wep key

I specified the mac , but still I can't obtain the key

---

### Post by master2010 on 2008-10-03
so nobody knows the solution to this problem

---

### Post by binbash on 2008-10-03
> **master2010 said:**
> so nobody knows the solution to this problem

Can you please paste the command which you used to collect the IVs.(exact command)

---

### Post by master2010 on 2008-10-03
sudo airodump-ng --bssid 00:11:95:3E:5C:A3 --channel 6 --write 1987 ath0

---

### Post by binbash on 2008-10-03
There is nothing wrong with airodump-ng command.can you please also post your  aireplay-ng command which you are injecting packages.

---

### Post by master2010 on 2008-10-03
sudo aireplay-ng -3 -e D-Link ath0

sudo aireplay-ng -1 0 -e D-Link ath0

sudo aireplay-ng -0 10 -e D-Link ath0

thanks for replying

---

### Post by sinclair86 on 2008-10-03
are you sure you are authenticated with the AP.  aireplay-ng -1 0 -e [ESSID] -a [BSSID] ath0 if it doesnt have mac filtering and  aireplay-ng -1 0 -e [ESSID] -a [BSSID mac] -h [mac of adddress of a an authenticated computer] ath0. also another thing that was screwing me up was when i was doing airmon-ng start wifi0 without a channel [eg airmon-ng start wifi0 6] i wasnt able to crack my own AP. you should pull out tcpdump and | grep with it to look for deauth packets.

---

### Post by master2010 on 2008-10-04
Sorry, but how and when to use Tcpdump?

---

