---
title: "user password &amp; login issues"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Xenomorph05 on 2010-07-06
Hey I have some weird "bugs" going on. I cant get ubuntu to ask for a password on startup. It always auto login. I even go to users and groups and change password. 

My second issue I think might be related but when I go to Time & Date I can't unlock it. Pressing the unlock button does nothing.

Thanks, I'm half tempted to do a fresh install of 10.04....

---

### Post by nothingspecial on 2010-07-06
In your menus, go System > Administration > Login Window

Uncheck the automatic login box

---

### Post by Xenomorph05 on 2010-07-06
I can't do that. When I press unluck it doesn't do anything at all. It's like I dont have permission to change settings.

---

### Post by sisco311 on 2010-07-06
Please open a terminal and post the output of:
```
pkexec echo polkit
```
and
```
groups
```

---

### Post by Xenomorph05 on 2010-07-06
output: Error executing command as another user: No authentication agent was found.
& :  adm dialout cdrom plugdev lpadmin admin sambashare

---

### Post by nothingspecial on 2010-07-06
> **Xenomorph05 said:**
> I can't do that. When I press unluck it doesn't do anything at all. It's like I dont have permission to change settings.

Are you using an admin account?

---

### Post by Xenomorph05 on 2010-07-06
> **nothingspecial said:**
> Are you using an admin account?

When I installed ubuntu I only made this account, there are no others.

---

### Post by sisco311 on 2010-07-06
> **Xenomorph05 said:**
> output: Error executing command as another user: No authentication agent was found.
& :  adm dialout cdrom plugdev lpadmin admin sambashare

Press Alt+F2 and run:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

Then try to unlock *Date & Time* or *Login Window*. If it works then go to System -> Preferences -> Startup Applications and make sure that polkit-gnome-authentication-agent-1 is started at login time.

---

### Post by Xenomorph05 on 2010-07-06
> **sisco311 said:**
> Press Alt+F2 and run:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```Then try to unlock *Date & Time* or *Login Window*. If it works then go to System -> Preferences -> Startup Applications and make sure that polkit-gnome-authentication-agent-1 is started at login time.

wow that seems to have fixed it but I don't see "polkit" on startup list. I'll restart and check again. Why might this have happaned to me?

---

### Post by Xenomorph05 on 2010-07-06
when I restarted I couldn't modufy settings again untill I ran that polkit thing again.

---

### Post by sisco311 on 2010-07-06
Try to add the authentication agent manually to the Startup Applications, either via the GUI or the terminal:
```
mkdir -p ~/.config/autostart/
cp /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop ~/.config/autostart/
sed -i 's/NoDisplay=true/NoDisplay=false/' ~/.config/autostart/polkit-gnome-authentication-agent-1.desktop

```

EDIT2: never mind. :)

---

### Post by Xenomorph05 on 2010-07-06
> **sisco311 said:**
> Try to add the authentication agent manually to the Startup Applications, either via the GUI or the terminal:
```
mkdir -p ~/.config/autostart/
cp /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop ~/.config/autostart/
sed -i 's/NoDisplay=true/NoDisplay=false/' ~/.config/autostart/polkit-gnome-authentication-agent-1.desktop

```

Thanks! It seems to be all good now, What might have I done to have caused this to break?

---

### Post by sisco311 on 2010-07-06
> **Xenomorph05 said:**
> Thanks! 


You're welcome!

> **Xenomorph05 said:**
> 
It seems to be all good now, What might have I done to have caused this to break?

To be honest i have no idea.

---

