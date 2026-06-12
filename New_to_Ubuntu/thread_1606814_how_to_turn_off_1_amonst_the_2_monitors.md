---
title: "how to turn off 1 amonst the 2 monitors"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by sumanthhv on 2010-10-27
dear forum members,
 
I recently installed Ubuntu 10.10 recently. I have a laptop whose monitor is not working (emits a white screen display all the time). I've connected an external monitor for this purpose. In windows, the intel software allows me to switch off my laptop screen (thus avoiding the irritating white glare). But in Ubuntu, both the monitors are on all the time. I couldn't see any option to this effect in monitor utility. Can anyone help me in this?
 
Thanks in advance

---

### Post by ubudog on 2010-10-27
Go to System>Preferences>Power Management.  Click on the AC tab.  Set the "When laptop lid is closed" to blank screen.  Same in the Battery tab.  Then, simply close the laptop lid.  :)

---

### Post by sumanthhv on 2010-10-27
ubudog, thanks for the quick reply. But, if i close the lid, i wouldn't be able to use the keyboard.

---

### Post by ubudog on 2010-10-27
> **sumanthhv said:**
> ubudog, thanks for the quick reply. But, if i close the lid, i wouldn't be able to use the keyboard.

Ah, I thought you were using an external keyboard.  That is the only way I can think of to have that work.  If you can, get an external keyboard.

---

### Post by sumanthhv on 2010-10-27
> **ubudog said:**
> Ah, I thought you were using an external keyboard. That is the only way I can think of to have that work. If you can, get an external keyboard.
 
When my laptop boots, only external monitor is active. Its only when ubuntu fires up, that both my monitors turn on. So, i think tweaking something in ubuntu mite help.

---

### Post by mikewhatever on 2010-10-27
We could try disabling the output for the laptop monitor. Can you post the output of **xrandr** from Terminal.

---

### Post by ofb on 2010-10-27
sumanthhv, I'm using 10.4 so forgive me if this doesn't apply.

Go System > Preferences > Monitor

On the Monitor Preferences panel you'll see two squares representing the two monitors. Click the Laptop one to select it. Now on the right side of the panel you'll have two buttons to select On or Off for that display.

That's all. Select Off, and the Laptop display will turn on briefly at each boot, then will shut off as the Ubuntu desktop loads. Works flawlessly with my laptop here.


(PS - ubudog, you don't want to recommend closing the lid. That puts most laptops into sleep mode. ;) )

---

### Post by sumanthhv on 2010-10-27
> **ofb said:**
> sumanthhv, I'm using 10.4 so forgive me if this doesn't apply.

Go System > Preferences > Monitor

On the Monitor Preferences panel you'll see two squares representing the two monitors. Click the Laptop one to select it. Now on the right side of the panel you'll have two buttons to select On or Off for that display.

That's all. Select Off, and the Laptop display will turn on briefly at each boot, then will shut off as the Ubuntu desktop loads. Works flawlessly with my laptop here.


(PS - ubudog, you don't want to recommend closing the lid. That puts most laptops into sleep mode. ;) )

This worked perfectly. Thank you very much. Actually, the option "send same image to both monitors" was selected. So, i was not getting both the monitor and laptop. when deselected that option, i was able to switch off my laptop screen.

---

### Post by ubudog on 2010-10-27
> **ofb said:**
> (PS - ubudog, you don't want to recommend closing the lid. That puts most laptops into sleep mode. ;) )

That's why I said to set it to "Blank Screen" when the laptop lid closes.  But I think he got it fixed anyway. :)

---

### Post by ofb on 2010-10-27
> **ubudog said:**
> That's why I said to set it to "Blank Screen" when the laptop lid closes.

doh! I really shouldn't post here at 3AM.

---

### Post by ubudog on 2010-10-27
> **ofb said:**
> doh! I really shouldn't post here at 3AM.

:lolflag:  I know how you feel.

---

### Post by Shadow15991 on 2010-10-27
just open system > preferences > monitor. it should show the two monitors. you can toggle between monitors and select on - off . simple, isn't it?

---

### Post by ubudog on 2010-10-27
> **Shadow15991 said:**
> just open system > preferences > monitor. it should show the two monitors. you can toggle between monitors and select on - off . simple, isn't it?

:lolflag:  Forgot about that...

---

