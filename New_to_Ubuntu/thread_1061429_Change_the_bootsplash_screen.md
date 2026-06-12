---
title: "Change the boot/splash screen?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by funky_uncle on 2009-02-05
I see places like gnome-look.org has lots of splash screens, but they all seem to be for the part where the you see the orange bar getting filled. I'm fine with that, but *before* that splash screen, there's another, which shows only "Ubuntu" and the logo, and that's what I'd like to change somehow (I have a wide screen so the logo is all stretched and oval).

---

### Post by spiderbatdad on 2009-02-05
System>>Administration>>Login Window>>Local(tab). You can usually drag and drop the tar.gz file into this window or use the Add button. Then select the theme. You are looking for a gdm greeter theme.

---

### Post by leonardo_neo on 2009-02-05
Be careful though, 

Sometimes the login name, and password field doesn't show in the new GDM theme. And if you can't login, you can't boot, and if you can't boot, you can't change the setting!

Well, solutions are there for that too, but I am telling you this in advance, because I have had this bad experience, so just be careful for record.

Take care.

---

### Post by funky_uncle on 2009-02-05
> **spiderbatdad said:**
> System>>Administration>>Login Window>>Local(tab). You can usually drag and drop the tar.gz file into this window or use the Add button. Then select the theme. You are looking for a gdm greeter theme.I don't think that's it. There's a screen *before* the login screen, the one that comes right after the bios stuff.

---

### Post by mpsii on 2009-02-05
I believe you are looking for USplash or Bootsplash (something like that).

---

### Post by spiderbatdad on 2009-02-05
> **funky_uncle said:**
> I don't think that's it. There's a screen *before* the login screen, the one that comes right after the bios stuff.

GDM Greeters are the themes where you login username password options...

---

### Post by Arndtwe on 2009-02-12
> **funky_uncle said:**
> I don't think that's it. There's a screen *before* the login screen, the one that comes right after the bios stuff.

This is the usplash screen. I have had a lot of fun changing this on my system, there are a lot of them out there. What version of Ubuntu are you running? I am on 8.04 dell's mini 9 version. How I change mine is with these commands: First, copy the .SO to your desktop (when the whole process is over, you can just delete it from here) then open a terminal and type the following commands.
```
cd Desktop
```

```
sudo cp Theme.so /usr/lib/usplash
```
Just replace "Theme" with the name of the usplash you want

```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/Theme.so 10
```
once again replace "Theme" with the proper name

```
sudo update-alternatives --config usplash-artwork.so
```
Here a list will be presented with multiple choices and numbers next to each choice. Type the number next to the usplash you want then hit return

And last but not least, run this command in order to see the usplash at boot-up
```
sudo update-initramfs -u
```

Keep in mind that all this was done on a dell mini 9 running 8.04. I have no guarantees that this will work for you. Hope so though!! Good luck

---

