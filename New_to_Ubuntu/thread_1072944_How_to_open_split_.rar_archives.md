---
title: "How to open split *.rar archives"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Ben Page on 2009-02-17
As the thread name says, how to open split *.rar archives. I mean those many 14MB *.rar archives that are often in downloaded torrent folders. There are a few archives and there is a main archive (*.r01, *.r02...and *.rar) Any of these gives me an error when I click them. Is there a special app to open them? In win this is a common procedure, click the main extract and that's it! Is there a CLI way? Its annoying to have to boot win just to unrar...

---

### Post by altonbr on 2009-02-17
So long as you have 'unrar' installed, you can just extract *.r00 and it will extract the whole archive.

To install on the command-line, run:
```
sudo aptitude install unrar
```

---

### Post by trepid666 on 2009-02-17
Also, you only need to extract the file with extension .rar  It will extract them all. You don't need to extract the numbered ones

---

### Post by Ben Page on 2009-02-17
> **altonbr said:**
> So long as you have 'unrar' installed, you can just extract *.r00 and it will extract the whole archive.

To install on the command-line, run:
```
sudo aptitude install unrar
```

That worked, thnx, I have ARK installed, but it seemed it did not have rar support, only zip, by installing unrar, ark can now open rars.

I know, trepid666, done this a million times in windows, but thanx anyway.

---

