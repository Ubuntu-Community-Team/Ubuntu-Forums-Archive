---
title: "Firefox: Gmail loads blank page."
date: 2009-06-17
forum: New to Ubuntu
---

### Post by powel212 on 2009-06-17
In firefox lately when I open gmail I just get a blank white page. I found one blog entry telling me to clear my cache etc... I did that but am still getting the blank page. 

I am using Firefox 3.01
with gmail manager plugin

Any help is appreciated.

Powel

---

### Post by SOULRiDER on 2009-06-17
Can you try and load the plain HTML version at least?

Just in case, press ctrl + shift + del and clear everything once more. Also, try disabeling that plugin and see if it loads.

---

### Post by powel212 on 2009-06-17
```
Can you try and load the plain HTML version at least?

Just in case, press ctrl + shift + del and clear everything once more. Also, try disabeling that plugin and see if it loads.
```

Load HTML version worked

ctrl + shift + del = no change - still blank

Disable plugin - still blank

odd indeed

Thanks

Powel

---

### Post by jenkinbr on 2009-06-17
Is this in Karmic?

I just noticed that you're running that according to your profile info.

---

### Post by powel212 on 2009-06-18
This problem is happening  in Jaunty.

I'm testing karmic in VBox. So far it is really quite un-buggy. Looking forward to the full release.

Powel

---

### Post by zeroseven0183 on 2009-06-18
Where there any changes you made in Firefox aside from the Gmail plugin? There could be another plugin working with the Gmail you have.

Do you mean Firefox version 3.0.11 or just 3.0.1? Try updating the version.

---

### Post by powel212 on 2009-06-18
I have not made any recent changes to Firefox or its plugins. 

Do we know what gmail uses? Flash or Java. Perhaps one of those has a broken package.

Although I installed the Firefox 3.5Beta and gmail is working in it so I still think it is isolated to Firefox 3.01.

Gmail is also working in Epiphany without any problems.

Very odd indeed.

Powel

---

### Post by powel212 on 2009-06-18
Am I alone on this one? Nobody else experience this?

Thanks for all the help and any more help is certainly apreciated.

Powel

---

### Post by LewRockwell on 2009-06-18
> **powel212 said:**
> I have not made any recent changes to Firefox or its plugins. 

Do we know what gmail uses? Flash or Java. Perhaps one of those has a broken package.

Although I installed the Firefox 3.5Beta and gmail is working in it so I still think it is isolated to Firefox 3.01.

Gmail is also working in Epiphany without any problems.

Very odd indeed.

Powel

so you're using the gmail plug-in successfully in 3.5beta?

or did you mean to say something else?

---

### Post by powel212 on 2009-06-18
Not using the plug-in in 3.5

Plain old firefox 3.5 loads gmail just fine.

but

Firefox 3.01 with or without the plugin won't load standard gmail - will only load html only

P.

---

### Post by zeroseven0183 on 2009-06-18
I'd suggest you try a complete reinstallation of Firefox from either Synaptics or Add/Remove...

---

### Post by SOULRiDER on 2009-06-18
It may be a bug in Firefox's javascript engine (?).

Id suggest upgrading Firefox and just forgetting about it, im running 9.04 and have Firefox 3.0.11 and gmail works fine.

---

### Post by powel212 on 2009-06-20
Fixed: Working now.

The steps that made it work.

Disable gmail manager plugin
clear all cache and history...
restart firefox

still not working...

restart Jaunty - launch Firefox

Works

Powel

retest: re-enable gmail manager
still works until i switch gmail user.
then it just opens a blank page.
Re-disable gmail manager
restart firefox
Works again.

Conclusion, some problem with the gmail manager plugin.

---

