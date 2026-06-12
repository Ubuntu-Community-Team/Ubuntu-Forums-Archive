---
title: "Firefox 3 + Java"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by missmaryrules on 2008-09-06
I'm running Firefox 3 on Ubuntu 8.04 and it won't open java links, i.e. if the link is something like "javascript:editBankAccountForm1.submit()". When I click on the links, nothing happens; No windows open, the current window doesn't load another page, no error messages.

Also, I'm still having problems with flash and websites such as Citicards . c o m. I already posted about it in [this thread]("http://ubuntuforums.org/showthread.php?p=5730453#post5730453").

I really want to get these bugs worked out so I can get rid of Vista completely :(

---

### Post by Qloor on 2008-09-07
> **kubug said:**
> ...(Enter in your terminal)

```
sudo update-alternatives --config xulrunner-1.9-javaplugin.so

```

After entering your password, you will get prompted with something like this:

Select 2, or which ever has "java-6-sun" in it, and press enter.

Now, close firefox and start it back up. Check to see if you got the plug-in now by entering "about:plugins" in the address bar (without quotes)....

Try that.

---

### Post by missmaryrules on 2008-09-07
> **Qloor said:**
> Try that.



I tried it. I didn't get to the "Select 2" part or anything with "java-6-sun". Instead, I got:

```
No alternatives for xulrunner-1.9-javaplugin.so.

```

---

### Post by jamesstansell on 2008-09-08
Try
```
$ sudo apt-get install sun-java6-plugin
$ sudo update-java-alternatives -s java-6-sun
```

---

### Post by gamnoparts on 2008-10-31
Anybody have any luck on this?  I tried both suggestions above & got nowhere.

---

### Post by ppk3 on 2008-11-01
The problem of citicards page is caused by java-script.

If I go to edit-->preferences-->content, then uncheck the Enable JavaScript, then reload the citicards page. 

Then everything seems OK.

But you must set the enable javescript back to check before you login.

It's a bad solution. But I don't know which one cause the problem: Ubuntu? Firefox? Sun Jave? or citi?

---

### Post by jamesstansell on 2008-11-02
> **gamnoparts said:**
> Anybody have any luck on this?  I tried both suggestions above & got nowhere.

If you are running a 64-bit system then see the 64-bit forum for java help.

Otherwise, tell us more specifically what error you have, what you tried, and what the results were.

-james.

---

