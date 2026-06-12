---
title: "Java will not work at my browsers, inkluding Firefox"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Pinon on 2010-01-21
I cannot log into my bank, which uses a javascript for users to log in.

Java does not work at my browsers.

When I at the Terminal type:
johnny@johnny-laptop:~$ java -version

I get the following result:
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02, mixed mode, sharing)

It used to work earlier, but after a system update, it no longer work. At least I think that is the reason why java does no longer work, not at firefox, nor at for example the chromium browser.

---

### Post by USB_NL on 2010-01-21
dos this help/work:

```
sudo apt-get install ubuntu-restricted-extras
```

?

maby it will help if you give more info

---

### Post by Pinon on 2010-01-22
When 
sudo apt-get install ubuntu-restricted-extras

I get
sudo apt-get install ubuntu-restricted-extras is already newest version.

Yes, more information would of course be good here, but I am not sure what information that is most important to post.

By the way, I found out that my Opera browser in fact supports Java.

The others don't though. I like to use Firefox so it would be nice if it supported Java.

when I from FireFox (Namoroka 3.6) do
Tools | Addons | Get Addons | then search for "java" | Cliks Java Console 6.0.02 | Add to Namoroka (I installs the java console) | Accept | Install | Restarts Namoroka...

Then I recieve this ERROR MESSAGE:

/ quote

The Java Console extension is no longer supported and will be automatically removed the next time you restart Firefox.  This will not affect any Java applications or websites in any way.

Do you want to restart Firefox now?

/ unquote

I do not know if this information was helpful though :p

---

