---
title: "More of a firefox problem then Ubuntu..."
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Li18nxBoy on 2009-06-08
I am trying to get the 811.com tool-bar installed but I get this error:


"811 Toolbar" will not be installed because it does not provide secure updates


Is there anything I can do about this

(I tried google with no luck)

---

### Post by QIII on 2009-06-08
Are you sure you want to disarm the plugin security checks?

There is a reason you are getting this message.  It's not an error.

---

### Post by Li18nxBoy on 2009-06-08
For a while yes, I want it back up once Im done installing it...

---

### Post by furialis on 2009-06-08
Is [this]("https://addons.mozilla.org/en-US/firefox/addon/5017") what you want to install?

---

### Post by Li18nxBoy on 2009-06-08
> **furialis said:**
> Is [this]("https://addons.mozilla.org/en-US/firefox/addon/5017") what you want to install?

yes it is, I assume the add-on from the website is built for firefox 3.0
[URL="http://my.811.com/"]
http://my.811.com/[/URL]

---

### Post by QIII on 2009-06-08
It's experimental for FF3 according to mozilla.org.

---

### Post by Li18nxBoy on 2009-06-08
I got it install in firefox portable 2.0

I would still like it in my main browser if I could

---

### Post by QIII on 2009-06-08
OK.

I recommend AGAINST installing it, because the versions for FF2.0 dragged down browsing performance and people reported problems with how searches worked.

You are getting that error for the current version of that extension because mozilla doesn't have a secure way to update this version right now.  As I said, it's experimental in FF3.

Fair warning.

Open a new tab in FF.
Type about:config into Firefox’s address bar.
Click the “I’ll be careful, I promise!”.
Right click anywhere in the list.
Click New.
Click Boolean.
Type "extensions.checkUpdateSecurity" in the Enter the preference name box.
Click False.
Restart Firefox.

Try to install your extension.

Remember that you have just disabled a valuable warning in FF.

---

### Post by Li18nxBoy on 2009-06-08
Firefox became unstable and almost locked up my system, taking nearly 3gig or ram and all my CPU. I removed the add on and turned the security stuff back on.

I got it working with Ffirefox 2.0 portable under wine nice and clean, so I'm happy with that.



thanks for your help guys

---

