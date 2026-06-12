---
title: "Wireless keyring."
date: 2010-04-13
forum: New to Ubuntu
---

### Post by ericeclifford on 2010-04-13
Say if my router requires a password to get on to the wireless network.

I am on a ISO image of ubuntu off a USB stick with grub.

The default.keyring in gnome2, holds the password of the wireless network right?

So, if I save my keyring file to the USB stick, and tell my startup script to move that file upon startup to the right place(gnome2), it shouldn't ask me to reenter password correct?

---

### Post by WinterRain on 2010-04-13
The only way I know to have ubuntu *not* ask for the password is to delete the login.keyring file, then it will ask you to input another one next time you use it, and then enter nothing. It will then ask you if you want to use unsafe storage. It will then never ask you again.

---

### Post by ericeclifford on 2010-04-13
> **WinterRain said:**
> The only way I know to have ubuntu *not* ask for the password is to delete the login.keyring file, then it will ask you to input another one next time you use it, and then enter nothing. It will then ask you if you want to use unsafe storage. It will then never ask you again.

But iso images wont save that config :(.

Isnt there a file I can put to the side and have a startup script auto login?

---

### Post by WinterRain on 2010-04-13
If you created the usb install with startup disk creator, it should remember any changes. At least it does for me.

---

### Post by mcduck on 2010-04-13
> **WinterRain said:**
> The only way I know to have ubuntu *not* ask for the password is to delete the login.keyring file, then it will ask you to input another one next time you use it, and then enter nothing. It will then ask you if you want to use unsafe storage. It will then never ask you again.

You don't need to delete the keyring file to do that, just use the keyring manager to change the password (or remove it). You'll find it in Applications/Accessories/Passwords and Encryption Keys.

What comes to the original problem, if you create your USB install with Unetbootin or Ubuntu's own tool (System/Administration/USB Startup Disk Creator) you'll have an option to use available space on the USB drive to create a persisten install. This allows you to store any settings you make, programs you install and of course your files as well on the USB drive (while still keeping it as a live-disk you can run on any computer).

---

### Post by ericeclifford on 2010-04-13
> **mcduck said:**
> You don't need to delete the keyring file to do that, just use the keyring manager to change the password (or remove it). You'll find it in Applications/Accessories/Passwords and Encryption Keys.

What comes to the original problem, if you create your USB install with Unetbootin or Ubuntu's own tool (System/Administration/USB Startup Disk Creator) you'll have an option to use available space on the USB drive to create a persisten install. This allows you to store any settings you make, programs you install and of course your files as well on the USB drive (while still keeping it as a live-disk you can run on any computer).

is there a way i can code my own persistence, so I can just save the file that is needed for wireless login, and replace it on next bootup with a program i made?

---

### Post by mcduck on 2010-04-13
> **ericeclifford said:**
> is there a way i can code my own persistence, so I can just save the file that is needed for wireless login, and replace it on next bootup with a program i made?
If you have some mad Linux-hacking skills then the answer is yes, otherwise no. :)

In other words there is no existing way to do such thing, and  can't really imagene why you'd want to go through the trouble of hacking such a solution when the persistent install solves all that kind of problems. If you are worried about not being able to use the USB drive for other purposes, the amount of space used for the persistence file can of course be adjusted, just give it bit of space and you'll be able to save (or change) your keyring password.

---

### Post by ericeclifford on 2010-04-13
> **mcduck said:**
> If you have some mad Linux-hacking skills then the answer is yes, otherwise no. :)

In other words there is no existing way to do such thing, and  can't really imagene why you'd want to go through the trouble of hacking such a solution when the persistent install solves all that kind of problems. If you are worried about not being able to use the USB drive for other purposes, the amount of space used for the persistence file can of course be adjusted, just give it bit of space and you'll be able to save (or change) your keyring password.

I just dont get what persistence does that I cant do with a startup script or a C program that I have running as a service in the background of my iso image, and I am using 8.04.2.

I mean cant I just automate a program to save the keyring to the Isodevice(USB stick with Iso images) and then have it place it in the correct folder upon bootup, and maybe throw in a inet restart( whatever the job is that calls the wireless)

---

### Post by mcduck on 2010-04-13
> **ericeclifford said:**
> I just dont get what persistence does that I cant do with a startup script or a C program that I have running as a service in the background of my iso image, and I am using 8.04.2.

I mean cant I just automate a program to save the keyring to the Isodevice(USB stick with Iso images) and then have it place it in the correct folder upon bootup, and maybe throw in a inet restart( whatever the job is that calls the wireless)

Well, if you are able to, then of course you can. I just can't see why to go through all that trouble to solve a problem when there's already a working solution to it.

Of course if you want to do such thing, and need help with it, you should definitely ask somewhere else than in the "Absolute Beginner"-section of these forums... ;)

---

### Post by ericeclifford on 2010-04-19
Does anyone know if I have the right file to save( the key ring)

I just entered a pass to a fresh boot up of a live dvd I customized, entered a PW to wireless, and it didnt even create the keyring.

---

### Post by gerryex on 2010-04-19
> **mcduck said:**
> You don't need to delete the keyring file to do that, just use the keyring manager to change the password (or remove it). You'll find it in Applications/Accessories/Passwords and Encryption Keys.
 
Hello,
 
My wireless router does have a secret phrase for encryption which I want, but I would like to not have to enter any password for the Keyring every time I boot up. I went into Applications/Accessories/Passwords and Encryption Keys as you suggested but I did not find any mention of a Keyring Manager and the only password it had was the one for the router encryption. Did I not look in the right place?
 
Thanks,
Gerry

---

### Post by mcduck on 2010-04-19
> **gerryex said:**
> Hello,
 
My wireless router does have a secret phrase for encryption which I want, but I would like to not have to enter any password for the Keyring every time I boot up. I went into Applications/Accessories/Passwords and Encryption Keys as you suggested but I did not find any mention of a Keyring Manager and the only password it had was the one for the router encryption. Did I not look in the right place?
 
Thanks,
Gerry

The program that opens when you go to Applications/Accessories/Passwords and Encryption Keys *is* the keyring manager. :)

Anyway, I doubt that your wireless router's password would be saved in the keyring, most likely you access the router's configuration using your web browser, so it's the *browser* that's saving that password for you.

If you use Firefox as your browser go to Edit/Preferences and take a look at the Security-tab. You'll find options to enable/disable saving of passwords, enable/disable master password, and a "Saved Passwords"-button that allows you to view the passwords Firefox has saved.

---

### Post by gerryex on 2010-04-19
> **mcduck said:**
> The program that opens when you go to Applications/Accessories/Passwords and Encryption Keys *is* the keyring manager. :)
 
Anyway, I doubt that your wireless router's password would be saved in the keyring, most likely you access the router's configuration using your web browser, so it's the *browser* that's saving that password for you.
 
If you use Firefox as your browser go to Edit/Preferences and take a look at the Security-tab. You'll find options to enable/disable saving of passwords, enable/disable master password, and a "Saved Passwords"-button that allows you to view the passwords Firefox has saved.
 
 
Hello,
 
Thanks for getting back to me so quickly!!
 
But . . . when I looked in the various tabs there was only one password listed and when I opened it up it stated that it was the secret phrase for the wirelss router and when I showed the actual password it was the phrase that I set up into the router. It was not the single password that I have to enter everytime I boot up. A few seconds after U boots up I get a pop box labeled something about keyring and asking for the single password which I enter. Then it connects with the wireless router. This single password entry is the one I would like to not have to do.
 
Thanks again,
Gerry

---

### Post by ericeclifford on 2010-04-19
> **gerryex said:**
> Hello,
 
Thanks for getting back to me so quickly!!
 
But . . . when I looked in the various tabs there was only one password listed and when I opened it up it stated that it was the secret phrase for the wirelss router and when I showed the actual password it was the phrase that I set up into the router. It was not the single password that I have to enter everytime I boot up. A few seconds after U boots up I get a pop box labeled something about keyring and asking for the single password which I enter. Then it connects with the wireless router. This single password entry is the one I would like to not have to do.
 
Thanks again,
Gerry


Same, this is the WPA password that you need to enter to get into secure networks.

Is there a program that saves this in a config file, that I can then use as a persistence file to keep my iso image on my USB up to date at boot up everytime?

---

### Post by mcduck on 2010-04-19
> **gerryex said:**
> Hello,
 
Thanks for getting back to me so quickly!!
 
But . . . when I looked in the various tabs there was only one password listed and when I opened it up it stated that it was the secret phrase for the wirelss router and when I showed the actual password it was the phrase that I set up into the router. It was not the single password that I have to enter everytime I boot up. A few seconds after U boots up I get a pop box labeled something about keyring and asking for the single password which I enter. Then it connects with the wireless router. This single password entry is the one I would like to not have to do.
 
Thanks again,
Gerry

So you are indeed talking about the wireless network's password, not the router's password. In that case it is stored in the keyring, and here are the exact steps to change/remove the keyring password:

1. Go to Applications/Accessories/Passwords and Encryption Keys
2. Right-click the "Passwords:login" -keyring and select "Change Password"
3. Type your old password, and leave the fields for new one empty.

---

### Post by ericeclifford on 2010-04-19
> **mcduck said:**
> So you are indeed talking about the wireless network's password, not the router's password. In that case it is stored in the keyring, and here are the exact steps to change/remove the keyring password:

1. Go to Applications/Accessories/Passwords and Encryption Keys
2. Right-click the "Passwords:login" -keyring and select "Change Password"
3. Type your old password, and leave the fields for new one empty.

If it is the routers password( no login, just password for WPA)

I couldnt find it in edit/preferences in the firefox browser, under the security tab.

I guess the WPA password(routers password for wireless) is not stored in the file system, but the router itself? hence being impossible to keep it logged in if you are using an live iso image OS?

I dont think the browser saves the routers wireless password.

---

### Post by mcduck on 2010-04-19
> **ericeclifford said:**
> If it is the routers password( no login, just password for WPA)

I couldnt find it in edit/preferences in the firefox browser, under the security tab.

I guess the WPA password(routers password for wireless) is not stored in the file system, but the router itself? hence being impossible to keep it logged in if you are using an live iso image OS?

I dont think the browser saves the routers wireless password.

I'll try to make this as clear as possible.

You have different passwords:

**router's password** would be the* password to access the router's configuration*. In most cases you'd do that using your web browser, so the password would be saved in the web browser.
[B]
Wireless network's password [/B] would be the [I]password used to connect to a wireless network
[/I] (the WEB, WPA or whatever password). This is stored in the keyring.

**Keyring password** is the password used to unlock the keyring.

**You** are having problems with the **wireless network's password** and **keyring password** (and I have already given you the only solution to your problem I'm able to give you) 

**gerryex** I'm not sure about which password he's actually having problems with as he started taklking about router's password but it seems that he actually meant wireless network's password. I have now given solution to each of these passwords in this thread. One of these solutions will fix his problem, depending of course on which password he was actually talking about.

---

### Post by gerryex on 2010-04-19
> **mcduck said:**
> 
**gerryex** I'm not sure about which password he's actually having problems with as he started taklking about router's password but it seems that he actually meant wireless network's password. I have now given solution to each of these passwords in this thread. One of these solutions will fix his problem, depending of course on which password he was actually talking about.
 
Hi mcduck,
 
Success!!! Yes, the WPA password (or phrase) is stored in the router. To gain access to the physical hardware router to change its settings you use a browser and the router's password is stored there. But the password I wanted to eliminate was to unlock the Keyring, and your procedure worked. It warned me about unsafe storage of passwords using a blank Keyring password but I said OK anyway. Then I re-booted, and the wireless network connected without asking me for a password, which is what I wanted!!
 
Thanks again!
Gerry

---

### Post by xumuk37 on 2010-04-19
all keyring settings are in ~/gnome2/keyrings or GUI way Applications --> Accesories --> Passwords and Encription Keys

---

