---
title: "ubuntu lucid lynx will not boot"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by pete79 on 2010-07-02
i have just updated lucid lynx and now after the restart i cannot boot into ubuntu,i also have windows 7 on the same system which is fine as this is were im sending this message from, i need help please

---

### Post by Rubi1200 on 2010-07-02
Could you please provide us with some more information?

How did you install Ubuntu, with a LiveCD or via Wubi?

What are your computer specs., e.g. model, RAM, graphics card etc.

The more you tell us, the better we can help you.

---

### Post by sahabcse on 2010-07-02
paste the error information

---

### Post by pete79 on 2010-07-02
spec: 

[LIST]
[*]AMD Turion II Dual-Core M620  processor
[*]4GB RAM
[*]500GB hard drive
[*]15.6in  HD Brightview display
[*]LightScribe SuperMulti optical drive
[*]ATI Radeon HD 4200 graphics
[*]WiFi - 802.11 b/g/n
[*]Webcam with microphone
[*]Bluetooth
[*]4  USB 2.0 ports
[*]IEEE 1394 FireWire interface
[*]10/100/1000  Gigabit Ethernet LAN
[*]Windows 7 Premium
[*]6-cell  Lithium-Ion rechargeable battery
[*]Espresso Imprint neoprene  carry case
[/LIST]
  the error message is error: unknown command 'loadfont'.
                                error:  unknown command type

unitl i updated it was working fine
 
 
[IMG]http://www.kays.com/images/product-promo-logos/1_25_off_warranty.gif[/IMG]

[]("http://javascript%3Cb%3E%3C/b%3E:readReviews%28%29;")

---

### Post by pete79 on 2010-07-02
m

---

### Post by pete79 on 2010-07-02
oh yeah installed straight from the website

---

### Post by Rubi1200 on 2010-07-02
> **pete79 said:**
> oh yeah installed straight from the website

I am assuming this means you installed with Wubi:

[http://wubi-installer.org/index.php](http://wubi-installer.org/index.php)

Do you have an Ubuntu CD or could you get hold of one?

---

### Post by pete79 on 2010-07-02
yeah wubi sounds familiar,dont have a cd and dont think i can get one anywere,could i download it straight from the website and then burn it to disc and try it that way

---

### Post by Rubi1200 on 2010-07-02
> **pete79 said:**
> yeah wubi sounds familiar,dont have a cd and dont think i can get one anywere,could i download it straight from the website and then burn it to disc and try it that way

Perfect!

Once you have it burned to CD boot the computer (if needs be set BIOS to boot from CD) and choose the option to try Ubuntu rather than installing it.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here and we will see what can be done to help you resolve this.

---

### Post by pete79 on 2010-07-02
thanx man, already started the download,should be done in 10 to 15 mins,will post back results

---

### Post by pete79 on 2010-07-02
the link u have added wont work for me i used all the code you have there and nothing,says command not found, i have not installed it yet still trying, if i install it will it install over the original version i had installed or form a new one

---

### Post by Rubi1200 on 2010-07-02
> **pete79 said:**
> the link u have added wont work for me i used all the code you have there and nothing,says command not found, i have not installed it yet still trying, if i install it will it install over the original version i had installed or form a new one

Did you place the script on the Desktop?

Then:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This is a simple script, no installation required on the LiveCD.

If the above command does not work, try this:

```
su bash ~/Desktop/boot_info_script*.sh
```

---

