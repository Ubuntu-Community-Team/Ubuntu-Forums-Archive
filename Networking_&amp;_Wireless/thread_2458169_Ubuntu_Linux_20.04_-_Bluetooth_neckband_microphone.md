---
title: "Ubuntu Linux 20.04 - Bluetooth neckband microphone not working"
date: 2021-02-18
forum: Networking &amp; Wireless
---

### Post by la.khan on 2021-02-18
Hi all,

I own a Dell Inspiron 3543 laptop since June 2015. This laptop came with an integrated microphone. Recently, in Oct. 2020 IIRC, I had to record a short video message and I realized that the footage has static. My laptop currently has Ubuntu Linux 20.04 64 bit.

I used a pair of headphones + microphone to record a short video message. When I play back the footage, it has static. Maybe, behind the scenes, my headphones + microphone use the same integrated microphone and/or its drivers to record. So, no wonder the footage has static. BTW, I use application guvcview to access my integrated webcam to record footage. To me, it feels like the integrated microphone has a driver issue. I looked around in Google to see if there is a solution to my problem. Some posters suggested killing PulseAudio, specify the correct audio sample rate etc. I did these things and the static may have reduced but it is still there.

So, to circumvent the usage of the integrated microphone, I ordered a Bluetooth neckband with earphones and microphone. I could connect the neckband to my laptop effortlessly. The earphones work fine but the microphone doesn't. I recorded video footage but the footage has no audio; looks like no input to the microphone. I thought I received a defective neckband but when I paired the it with my Android mobile and made a call, the other person confirmed she could hear me. So, the microphone in the neckband works fine.

My configuration is - 
Laptop hardware: Dell Inspiron 3543 Intel(R) Core i5-5200U CPU @ 2.2 GHz x 4; 8GB RAM; 1 TB HDD
Neckband: Boult Audio ProBass FlowX, Bluetooth 5.0
Software: Ubuntu Linux 20.04 (64 bit), guvcview, VLC 3.0.12.1

When I look at arecord, I see
```
$arecord -l
**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC3234 Analog [ALC3234 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

So, is this a Bluetooth driver issue? How do I resolve this issue?  Please let me know if you need more information. I appreciate any  suggestions/pointers/insights. Thanks in advance for your help!

---

### Post by CelticWarrior on 2021-02-18
Not really a Bluetooth issue.
You need to understand how it works. Your neckband works with 2 different Bluetooth audio profiles, A2DP (Stereo HiFi, no microphone) or HFP (AKA "Hands Free", Mono LowFi + microphone). By default all similar devices pair using A2DP. Users need to manually select the other profile in order to use the microphone. Most work fine, some need additional steps and installation of additional software to be able to work as HFP in Ubuntu. Any phone, Android or iOS, has the ability to seamlessly toggle profiles, i.e., use A2DP by default for music/video apps and automatically switch to HFP in a call and then back to A2DP when the call has finished. Desktop Linux doesn't do that.

---

### Post by la.khan on 2021-02-18
@CelticWarrior: Thanks for the reply. In Ubuntu Settings -->Sound,  for output, when I choose my Bluetooth neckband, I see 2 different  configurations - A2DP & HSP/HFP. But I can't get my microphone to  work in either of them. Looks like I need to install additional software  to get my microphone to work. Do I need to install any application(s)  and/or driver(s)? Any specific recommendations?

---

### Post by CelticWarrior on 2021-02-18
Here are some ideas: [https://askubuntu.com/questions/922860/pairing-apple-airpods-as-headset](https://askubuntu.com/questions/922860/pairing-apple-airpods-as-headset)

---

### Post by la.khan on 2021-02-18
Thanks for the pointer. I have gone through this URL & other links this URL refers to. No luck. I have modified files, installed applications (VLC, Blueman, oFono), looked around for drivers and have made no progress :( After going through so many changes, I concluded that this needs to be fixed by Canonical/Ubuntu.

I did my own research and realized that this is a widespread problem in Ubuntu Linux universe. Since last few years. Down the years, UL users have come up with their own workarounds to make their BT hardware work with their OS installation. UL users have to jump through hoops to make their BT microphone work.

I am surprised that Ubuntu/Canonical haven't attended to this problem of Bluetooth A2DP/HSP/HFP and let it fester. Or, is it most hardware with UL OS works just fine with BT and my laptop hardware setup just happens to be an exception?

Any idea how it is with other Linux distros (Arch, CentOS, Debian, Fedora, Manjaro etc)? My Android 10 mobile works fine with my BT neckband. No fooling around for applications and/or drivers. What about other OSes (Windows, iOS)?

---

