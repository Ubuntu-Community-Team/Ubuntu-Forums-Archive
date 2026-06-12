---
title: "Need help using  ftp with GUI"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by mvalviar on 2009-01-25
I need to transfer some files to a remote web host and I tried to use "Connect to server..." under the places menu. I filled out the required fields and waited for nautilus to show it however it just displays the contents of the location for a fraction of a second then returns to my home folder. I wanted to use nautilus for ftp transfer so I can drap/drop and copy/paste. I can ftp with the terminal with out any problem. Anyone with a fix on this?

---

### Post by Michael.Godawski on 2009-01-25
hi,

why not use a graphical tool like gFTP? It's in the repos.

---

### Post by jnw222 on 2009-01-25
nautilus can ftp
type in
```
ftp://username@ftpsite.whatever
```

---

### Post by diablo75 on 2009-01-25
I click Places>Connect To Server.

Then change it from Public FTP to... I think it's FTP (with login).  Add in a username (the password will be asked for later), and a default folder to open up if you want one.  This is handy if you're a webmaster and never do anything outside your public_html folder (or whatever it might be called).

You can also create bookmarks after you've established a connection so in the future you can click on something like "My funky FTP" and it'll open it up right away.

Just re-read your post.... not sure why it's going away just a few seconds later.  Did you tell it to remember your password after entering it?

---

### Post by llamabr on 2009-01-25
Or jftp.

Also, given the choice, you might want to be using sftp, rather than ftp.  More secure (and hadled by jftp)

---

### Post by mvalviar on 2009-01-25
[QUOTE=diablo75;6614649]I click Places>Connect To Server.

Then change it from Public FTP to... I think it's FTP (with login).  Add in a username (the password will be asked for later), and a default folder to open up if you want one.  This is handy if you're a webmaster and never do anything outside your public_html folder (or whatever it might be called).

You can also create bookmarks after you've established a connection so in the future you can click on something like "My funky FTP" and it'll open it up right away.

That is how I do it too. It connects, pops out a nautilus window (showing my folders on that remote server) then it reverts back to my home folder. It also shows the mounted location briefly on the side pane.

I just tried typing the location on the address bar on nautilus. I does the same thing. I noticed that the location I mounted briefly because I see it appear on my desktop for a split second.

---

### Post by mvalviar on 2009-01-26
*bump*

I'm still in need of help on this. Thanks for all your suggestions. Still I want to use what is provided with ubuntu out of the box plus I also use gedit with the file viewer pane thats why I really need this to work.

---

