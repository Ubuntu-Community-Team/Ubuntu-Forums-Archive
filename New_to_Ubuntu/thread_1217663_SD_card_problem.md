---
title: "SD card problem"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Joe17 on 2009-07-19
I have a mini SD card which i use in my phone, and i transfer music onto it through my laptop (Acer Aspire One -Linux) or computer (windows computer).

Both mediums worked fine as i could drag and drop files into the memory stick as it came up.
However when i put my memory stick into my laptop only two folders come up and they have protected permissions on them. Which when i try to drop files in it does not let me.

People have said this is due to the SD card's slider, however i can use a USB Card reader or use my phone's cable and i still get the same response - only two protected folders come up.

Now with a low level of linux knowledge, i used the command chmod 777 then the memory sticks full file name. This returned the error that it cannot be done because it is a 'read-only file system'.

Could anybody help me please
Thankyou in advance

Also out of interest is my system XFCE? It is Linpus Lite on my laptop, but tat is not a prefix

---

### Post by rraj.be on 2009-07-19
Just type this in terminal

```
sudo nautilus
```

it will ask for your password, Enter it. But ubuntu wont display password for security reasons.

Now you have opened the Nautilus File manager in root mode.

Now you can copy or paste or delete any files in any place. But be careful.

---

### Post by teh603 on 2009-07-20
Administrator mode still won't beat a hardware write-protect, though. Or at least it shouldn't.

---

### Post by Joe17 on 2009-07-20
The command was sudo thunar on my system.
It still had the same output as before, with only the two folders showing up and no copy and paste.

Thanks for the suggestion though

---

### Post by presence1960 on 2009-07-20
did you try formatting the card and starting over? If you'd rather not format then...

if the folders have permissions then they are linux folders. Put the sd card into your linux machine and then run > gksu thunar Go to filesystem > media > (your flash card)entry. Right click on it and choose properties. Go to permissions tab and change the first 2 permissions for Owner & Group from root to your user name. Click apply permissions to enclosed files.

You may have to do the same from gksu thunar to the folders if that doesn't work on the folders. Just highlight your sd card on the left pane and do the same for those 2 folders.

---

### Post by Joe17 on 2009-07-20
No havent tried formatting, thought there would be a better alternative.

the gksu thunar returned

bash: gksu: command not found

Obviously cannot be used. Do you know any gksu command equivilant?

Thankyou

---

### Post by presence1960 on 2009-07-20
sudo thunar

---

### Post by Joe17 on 2009-07-20
Okay i formatted the SD card and it now works on my linux system.
To the command ls -l it returns with the correct permissions.

However if anybody could explain reasons this may have happened in the first place i would be very happy.

Thankyou

---

### Post by presence1960 on 2009-07-20
> **Joe17 said:**
> Okay i formatted the SD card and it now works on my linux system.
To the command ls -l it returns with the correct permissions.

However if anybody could explain reasons this may have happened in the first place i would be very happy.

Thankyou

Did you copy the files/folders over with root permissions in thunar?

---

### Post by Joe17 on 2009-07-21
No didnt copy the files over with root permissions. The SD card now works as it did before, with everything on the Memory card being recognised. 

Thanks for suggestiions

---

### Post by Kinger23 on 2009-07-23
Joe>
I've had the same problem with my AA1 both with Limpus Lite and now Ubuntu NBR.

I'd like to just reformat the SD Card but I can't seem to find out how here. What did you do to format the card? Did you use the expansion port or just the card reader?

---

