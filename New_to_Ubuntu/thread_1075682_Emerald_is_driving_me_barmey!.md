---
title: "Emerald is driving me barmey!"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-02-20
I'm trying to change themes in emerald but it just wont change even after restarting emerald:(

Please help!

---

### Post by ibuclaw on 2009-02-20
In **System->Preferences->CompizConfig Settings Manager**, scroll down to the **Effects** section and click **Window Decoration**. Ensure that the **Command** is:
```
/usr/bin/emerald --replace
```

Then press **Alt+F2** and use the same command again in the Run command box.

Regards
Iain

---

### Post by howefield on 2009-02-20
Try pressing the Alt + F2 keys together to get a run box, and type into it
```

emerald --replace
```

You can add this to your sessions menu if you want it start at boot.

---

### Post by jenkinbr on 2009-02-20
> **howefield said:**
> Try pressing the Alt + F2 keys together to get a run box, and type into it
```

emerald --replace
```

You can add this to your sessions menu if you want it start at boot.
+1

That was the only way I could make emerald be persistant in decorationg windows.

---

### Post by kamitsukai on 2009-02-20
Tried both of those and still nothing even after restart...

---

### Post by howefield on 2009-02-20
> **jenkinbr said:**
> That was the only way I could make emerald be persistant in decorationg windows.

I have it set via compiz similar to tinivole, only I don't use the "--replace".

Works fine with /usr/bin/emerald

---

### Post by ibuclaw on 2009-02-21
Alternately, you can install fusion-icon
```
sudo apt-get install fusion-icon
```

**Alt+F2**
```
fusion-icon
```

Then right-click on the new blue cube icon in the notification area and select:
**Select Window Decorator** -> **Emerald**
then
**Reload Window Manager**

Afterwards, you can quit/uninstall the app if it works and you are happy with it :)

Regards
Iain

---

### Post by kamitsukai on 2009-02-22
> **tinivole said:**
> Alternately, you can install fusion-icon
```
sudo apt-get install fusion-icon
```

**Alt+F2**
```
fusion-icon
```

Then right-click on the new blue cube icon in the notification area and select:
**Select Window Decorator** -> **Emerald**
then
**Reload Window Manager**

Afterwards, you can quit/uninstall the app if it works and you are happy with it :)

Regards
Iain

I currently already have fusion-icon installed;)but Emerald is just being buggy and stubborn:(

---

