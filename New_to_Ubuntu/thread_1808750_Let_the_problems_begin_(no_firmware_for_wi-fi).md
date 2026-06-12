---
title: "Let the problems begin (no firmware for wi-fi)"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-07-20
So, finally, after a long day, I managed to download, burn and install 11.04 on my laptop.
The laptop is an Acer aspire 5000, and I'm running Ubuntu exclusively. Upon startup, the OS let me know my hardware didn't support Unity, so I'm running the traditional layup.
Now, when I tried to set up my wireless, I found a "device not ready (firmware missing) sign.
In previous versions of Ubuntu, there was a way to use the CD to get the driver. I can't find it here. I tried the CD anyway, with no luck. Then, I tried the 9.10 CD, and got a pop up that pretty much guided me to find the driver, but, upon installing it, it tells me there's been an error, and nothing happens.

I don't have access to an ethernet connection. How can I get the b43 broadcom driver installed without it?

Thanks in advance. :)

---

### Post by bkratz on 2011-07-20
> **Inodoro Pereyra said:**
> So, finally, after a long day, I managed to download, burn and install 11.04 on my laptop.
The laptop is an Acer aspire 5000, and I'm running Ubuntu exclusively. Upon startup, the OS let me know my hardware didn't support Unity, so I'm running the traditional layup.
Now, when I tried to set up my wireless, I found a "device not ready (firmware missing) sign.
In previous versions of Ubuntu, there was a way to use the CD to get the driver. I can't find it here. I tried the CD anyway, with no luck. Then, I tried the 9.10 CD, and got a pop up that pretty much guided me to find the driver, but, upon installing it, it tells me there's been an error, and nothing happens.

I don't have access to an ethernet connection. How can I get the b43 broadcom driver installed without it?

Thanks in advance. :)

About 3/4 ths the way down the page is b43 without internet access.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by Inodoro Pereyra on 2011-07-20
Thanks Bkratz for the link. But it's not working.

Here's what I did: 
I downloaded the file, burned it to a CD, and copied it into the newly created "wireless" folder.
Then, I got to the terminal, and typed 

> sudo cp -r ~/wireless/* /lib/firmware/

In which "~" was the path for the wireless folder. Then I got the message:

> cp: cannot stat 'bernardo/wireless/*': No such file or directory

I have tried several different ways and paths, and nothing works. What am I doing wrong?:confused:

---

### Post by bkratz on 2011-07-20
The ~ means your home directory which is where Joseph wanted you to make the folder.



reference

[http://ubuntuforums.org/showpost.php?p=2294236&postcount=2](http://ubuntuforums.org/showpost.php?p=2294236&postcount=2)

---

### Post by Inodoro Pereyra on 2011-07-20
Yeah, that's what I did.

I tried bernardo/wireless/* , home/bernardo/wireless/* , bernardo/wireless/b43 , bernardo/wireless/b43/* , etc. Nothing works.:(

---

### Post by TBABill on 2011-07-20
In the live session, what happens if you ```
sudo apt-get install firmware-b43-installer b43-fwcutter
``` I can always get the STA driver going right from the LiveCD without an ethernet connection but I have not tried the b43. I'm just wondering if it's configured to see the CD as a repo and able to grab the firmware so the b43 can be activated.

---

### Post by MDguy on 2011-07-20
What happens if you try: 
```
sudo cp -r /home/bernardo/wireless/* /lib/firmware/
```
(with a slash before "home")?

---

### Post by Inodoro Pereyra on 2011-07-20
> **TBABill said:**
> In the live session, what happens if you ```
sudo apt-get install firmware-b43-installer b43-fwcutter
``` I can always get the STA driver going right from the LiveCD without an ethernet connection but I have not tried the b43. I'm just wondering if it's configured to see the CD as a repo and able to grab the firmware so the b43 can be activated.

Nothing. It tells me "Unable to locate package firmware-b43-installer"

> **MDguy said:**
> What happens if you try: 
```
sudo cp -r /home/bernardo/wireless/* /lib/firmware/
```(with a slash before "home")?

IT WORKED!!! Thanks MDguy!!!:biggrin:

---

### Post by Inodoro Pereyra on 2011-07-20
And now I have Internet!!!

Thanks again everybody!:D

---

