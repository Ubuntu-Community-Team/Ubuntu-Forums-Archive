---
title: "Copy paste between X windows and MS windows."
date: 2009-04-19
forum: New to Ubuntu
---

### Post by runnner on 2009-04-19
How can I do copy and paste between X windows and MS windows. Thanks!

---

### Post by _Purple_ on 2009-04-20
<--snip-->

---

### Post by mikechant on 2009-04-20
Do you mean you want to copy and paste files between a Ubuntu filesystem and a Windows filesystem while running either Windows or Ubuntu, or do you mean you are running both Windows and Ubuntu on the same PC at the same time with one in a VM (Virtual Machine) and you want to copy and paste text to/from the VM?

---

### Post by aeiah on 2009-04-20
or do you mean you're running an x windows application in a windows environment and want to paste text from one to the other?

---

### Post by runnner on 2009-04-21
> **aeiah said:**
> or do you mean you're running an x windows application in a windows environment and want to paste text from one to the other?
Yes, this one. I don't know how to do? Thanks!

---

### Post by ibuclaw on 2009-04-21
Sorry for my ignorance, I know what you mean when you say X window, and MS Windows, but you fail to mention the context of which you are running (virtually?) the X Window application in.

What are you running? Ubuntu in a VM? If so, what Virtual Manager are you using?

Regards
Iain

---

### Post by bolucpap on 2009-04-21
I believe the OP is running an XDMCP client (an X Server like Cygwin/X) on an MS Operating system. I found that while you can copy and paste text from VNC and RDP clients to windows explorer address bars and the like; and vice versa, that doesn't work in Cygwin/X, so I would also like an answer.

---

### Post by ibuclaw on 2009-04-21
> **bolucpap said:**
> I believe the OP is running an XDMCP client (an X Server like Cygwin/X) on an MS Operating system. I found that while you can copy and paste text from VNC and RDP clients to windows explorer address bars and the like; and vice versa, that doesn't work in Cygwin/X, so I would also like an answer.

Ahh, I get you now.

Never used cygwin myself, but this page says that there should be a "Quick Edit" mode. [http://www.gigascale.org/softdevel/faq/24.html](http://www.gigascale.org/softdevel/faq/24.html)

That or press Alt+Space, release, then press 'e' then 'p'. Which would be, again, quoting that page.

Regards
Iain

---

### Post by runnner on 2009-04-22
Thank you for your replies.
I tried to use Cygwin, it's difficult to use, and need to download a lot of packages. I am looking for some other easy to use.

---

### Post by bolucpap on 2009-04-22
Which X Client/Server are you using on the windows side? I had difficulty setting up Cygwin too, some servers provided one set of packages and the others different sets, but once it worked it provided the best functionality. I now need to install it to a new Windows PC, and the prospect scares me because of its unpredictability. If you can point me towards another free X Server/Client for Windows, it'd be much appreciated.

---

