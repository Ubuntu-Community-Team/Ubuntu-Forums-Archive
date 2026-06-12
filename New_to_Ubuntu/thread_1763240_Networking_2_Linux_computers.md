---
title: "Networking 2 Linux computers"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by jsl90 on 2011-05-20
Hello

How do i network to linux computers one is a desktop the other is a netbook.  I can see my windows network but when i click on the icon nothing is there.

Can somebody help me?

---

### Post by nothingspecial on 2011-05-20
Assuming you are running Ubuntu 11.04,

```
sudo apt-get install openssh-server
``` on both machines.

Open your file browser, on the top bar thingy, click file > connect to server

In the top box choose ssh

in the next box down put user@ipaddress

That is your user name on the other computer and the other computers ip address. If you don't know the ip address, go to the other computer and right click the network icon then choose connection information.

Add a bookmark (say for example desktop or netbook)

Then click connect.

Type the password (again the one of the other computer) and choose to remember it forever.

Repeat the process on the other computer.

From now on you will be able to access each one from the other one from the places menu in your file browser.

I hope that made sense.

---

### Post by jsl90 on 2011-05-20
Sorry i should of said i'm using ubuntu 10.04, thanks for the quick reply.

---

### Post by bolucpap on 2011-05-20
I think the original poster meant file sharing, rather than remote terminal.

[Edit]Oops, sorry. Seeing openssh I assumed it was about remote terminal.[Edit]

---

### Post by nothingspecial on 2011-05-20
Well in that case, the instructions are the same except that the connect to server option should be in your places menu :)

---

### Post by nothingspecial on 2011-05-20
> **bolucpap said:**
> I think the original poster meant file sharing, rather than remote terminal.

Where have I mentioned a remote terminal ? This is accessing your other computer through nautilus.

---

### Post by bolucpap on 2011-05-20
Sorry about that, I misread your post :-( A thousand apologies.

---

### Post by nothingspecial on 2011-05-20
No problem :P

---

### Post by jsl90 on 2011-05-20
Hi 
i did as was instructed accept it came up as a broken package any ideas.

---

### Post by nothingspecial on 2011-05-20
Try ```
sudo apt-get install -f
```

---

### Post by jsl90 on 2011-05-20
the broken package was on the netbook

"The following packages have unmet dependencies.
   openssh-server: Depends: openssh-client (= 1:5.3pl - 3ubuntu3) but 1:5.3pl -3ubuntu6 is to be installed
E: Broken packages

---

### Post by nothingspecial on 2011-05-20
> **jsl90 said:**
> the broken package was on the netbook

That's very strange. You should still be able to access the desktop from the netbook until we sort the broken packge.

---

