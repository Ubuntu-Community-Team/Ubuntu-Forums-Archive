---
title: "Working wireless but network setting password unstable"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by sofasurfer on 2008-04-22
I have been trying to get help installing WUSB54GC. I was close to finding the answer. But I decided to try Hardy in place of Gutsy. Surprise, surprise...IT WORKED immediately. However, every time I want to connect I have to go to system>administration>network and re-enter my password.

I can enter my password and this activates my connection. But, as soon as I close the windows where I entered the password, the password changes.

In other words, I enter a password (in this case, "xxxxx"). It shows up as 5 black dots. I can close the window and then immediately reopen it and my password now shows up as the entire text box being filled with black circles. Now, if I disconnect I must re-enter the password and I will have a connection but if I reopen the password window the password will be glitched again.

How can I stablize my password?

---

### Post by TwinStinger on 2008-04-22
I'm not alone then, have exactly the same problem.
Running Hardy RC on Hp Compaq 6910P with Intel wireless card.

If anyone has a solution I'll be more than happy.
Otherwise I'm not having any problems at all with my installation, so far :)

/TwinStinger

---

### Post by sofasurfer on 2008-04-22
What is the RC in Hardy rc?

Well, I think its this friday that the stable Hardy comes out. Maybe that will fix our problem. Then again, maybe stable hardy will not run my adapter. Its always something.

---

### Post by justin_acklin on 2008-04-22
Interesting, my problem is it won't remember that it's WPA2 -- it keeps the SSID and password ok but I have to go in and change it from WPA to WPA2 every time I boot.

---

### Post by babboo on 2008-04-22
Your password isn't being changed.  The number of characters is being masked.  For example - you enter a user name and password to log in - but if you checked the file (/etc/shadow) you will find your user name along with a long string of characters.  I doubt you are entering a 26 char password.  This is the hash output of your password.  In the same way the number of characters you enter for your wireless connection is being munged.

As to why your connection drops and you have to re-enter your password...

I'm having the same problem with Gutsy

---

### Post by sofasurfer on 2008-04-22
My router is an Belkin54g. My adapter which I have to keep entering the password on is a WUSB54GC. My other pc with a Trendnet adapter card does not have this problem.

Is the password nessessary? I mean, I configured the system with the password. Now, because of this problem I tried to delete the password. I was told that I MUST configure the system to use a password.

Is there a way around this?
Hmmmmmm......

---

### Post by sofasurfer on 2008-04-22
Is the whole purpose of this password to protect the network from unauthorized usage and thus requires re-entering every time? Or if this password SHOULD NOT require re-entering every time, what is its purpose? This is not the password required to change my network settings.

---

### Post by babboo on 2008-04-22
Is this the password used to connect to your ISP?

---

### Post by babboo on 2008-04-22
Sounds to me like your system (assuming a laptop) is not playing nice with the USB adapter.  You may want to check it is compatible with Linux.

---

### Post by sofasurfer on 2008-04-22
I had to go back and read up on how to configure this stuff so I could remember what it all means. So many passwords and codes and keys and configuration stuff with computers it sometimes overloads my brain.

The problematic password is actually the encryption key or security code. 

So, I reconfigured the Belkin router so that the security feature was disabled instead of set to WPA.

Next, I reconfigured the Trendnet adapter in my windows computer so that the security feature was disabled. 

So far so good. They connected.

Next, I tried to reconfigure the WUSB54GC adapter in my Linux computer to have the security feature turned off. Dang!!! There is no "disabled" option. It appears that the security feature is required. I'll have to go read up on this. It doesn't make sense that I can not turn off the encryption mode. Does it to you?

---

### Post by babboo on 2008-04-22
according to the UG you can select "Disabled" to not use security.  It's right after you check to use "Infrastructure" mode.

HTH

---

### Post by sofasurfer on 2008-04-22
Ah ha, but the users guide is referring to features on the software to be run under windows. Correct?

---

### Post by TwinStinger on 2008-04-23
I downloaded a new Hardy Release Candidate today and installed it on a friends HP Compaq 6910 (bought on the same occation) and everything that didn't work on min eworked on his. I'm using Foneras router and he's got an old 3COM but I don't think that's the reason tough. Gonna do an reinstall on mine when Hardy is released.

/

---

### Post by TwinStinger on 2008-04-24
By the way, i was trying to install wubi on my HP Compaq 6910P.
Since it worked on my friends laptop (also a HP Compaq 6910P)and not on mine I figured it was because of that the release installed on my friends laptop was a bit closer to the acctual release of Hardy.
 
So.... I couldn't simply wait for the Release, instead I did a few attempts (coff coff, about 5) to install the latter release on my laptop i order to make it work. Took some time before I came up with answer to my problem...

This worked for me on my HP Compaq 6910P with wubi.

Previously under Vista I disabled bluetooth since I don't use it, it seems that when doing so the wireless connections alltogether is disabled in bios (speculating) and when Vista starts, my HP wireless handler turns on only the WIFI connection.

So when I enabled Bluetooth and then installed wubi everything worked extremely well.

/ TwinStinger

---

