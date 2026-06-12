---
title: "[SOLVED] step by step on static IP for ubuntu ?"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by ~L~ on 2008-04-16
[http://textsnippets.com/posts/show/319](http://textsnippets.com/posts/show/319)
here it says write these things down but how do i save it? also can u tell me how to static IP on ubuntu or give me a good guide unlike the ones shown when i type it on google.
thanks
i know how to do it on windows but i am using ubuntu and ubuntu only (not dual boot or anything)
thanks a lot
edit: [http://i42.photobucket.com/albums/e310/Morgoth_Bauglir/dns.png](http://i42.photobucket.com/albums/e310/Morgoth_Bauglir/dns.png) what if i put that one ? How do I save these changes and will it work ?

---

### Post by vlatkop on 2008-04-16
First of all you need to be logged as root user or editing this file with sudo command.
Second, which editor are you using?
Pico editor is quite simple to use. Just enter this command:

```
sudo pico /etc/network/interfaces
```

And after the modifications you have made to this file, press Ctrl+X to Exit pico editor, and you will be asked if you want to save changes to this file before exiting. Here press Y, and after that you will be asked the file name to write. Here just press enter, do not modify anything. After you have successful set your static IP address you need to restart networking:

```
sudo /etc/init.d/networking restart
```

You can also check your settings by typing:

```
ifconfig
```

or:

```
ip adress show
```

P.S. I have seen on your screenshot that you are using nano editor which is improved pico editor.

---

### Post by ~L~ on 2008-04-16
> **vlatkop said:**
> First of all you need to be logged as root user or editing this file with sudo command.
Second, which editor are you using?
Pico editor is quite simple to use. Just enter this command:

```
sudo pico /etc/network/interfaces
```

And after the modifications you have made to this file, press Ctrl+X to Exit pico editor, and you will be asked if you want to save changes to this file before exiting. Here press Y, and after that you will be asked the file name to write. Here just press enter, do not modify anything. After you have successful set your static IP address you need to restart networking:

```
sudo /etc/init.d/networking restart
```

You can also check your settings by typing:

```
ifconfig
```

or:

```
ip adress show
```

P.S. I have seen on your screenshot that you are using nano editor which is improved pico editor.
Thanks a lot it worked with the first attempt  although I had to type something else for the editor to appear. I had to type 
sudo nano /etc/network/interfaces

---

