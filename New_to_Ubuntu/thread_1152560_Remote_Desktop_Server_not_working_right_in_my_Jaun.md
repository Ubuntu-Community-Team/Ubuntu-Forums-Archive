---
title: "Remote Desktop Server not working right in my Jaunty/Dell M6400"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by swarup on 2009-05-07
I have just loaded Jaunty onto my Dell Precision M6400, and want to use it as a server for a remote desktop. I have tried using Vinagre as well as tightvncserver, but the same problem arises regardless of which I use: the remote desktop can initiate a connection to my laptop, request permission, and achieve a connection. And the image on my laptop's screen immediately appears on the remote desktop's monitor-- as it should. But that initial image which gets transmitted, gets immediately fixed on the remote moniter and does not continue to update as the image on my laptop changes. Whatever the first image was, that is all that gets transmitted. 

One odd thing is that if I move the cursor on my laptop screen, the remove desktop moniter *will* see the cursor moving around. But if I open and close any applications, or *anything* I do on my laptop screen, nothing of that is visible to the remote desktop except that the cursor itself is moving.

My laptop can work just fine as the remote desktop and recieve images from the desktop of any other computer. But any other computer which tries to connect as the remote desktop to my laptop, will get only one fixed image.

I have Jaunty on another computer, and the remote desktop server is working fine on that one. But on my laptop it is not working. How can I trouble-shoot this?

---

### Post by pokogr on 2009-05-08
Hi there. There is a known bug for the combination of remote desktop and compiz. It has to do with the new xorg+compiz that Jaunty uses. A bad workaround is just to disable compiz on the remote computer.

---

### Post by swarup on 2009-05-08
> **pokogr said:**
> Hi there. There is a known bug for the combination of remote desktop and compiz. It has to do with the new xorg+compiz that Jaunty uses. A bad workaround is just to disable compiz on the remote computer.

It doesn't seem to me that this is the problem I have facing, for the following two reasons:

1. The remote computer (i.e. the computer that is *receiving* the desktop) does not use Jaunty.

2. I do not have compiz enabled that I know of, on either computer. At least, so far as I know. I never enabled it, and I never use it. *(edit: I have just googled compiz-ubuntu, and compiz definitely does not come enabled on ubuntu's install. Which means compiz is not enabled on any of these computers we are using.)*

If my problem is indeed a bug related with Jaunty, then it has to be related with the *sending* computer (i.e. the server computer) and not the receiver (remote) computer. Because the server computer is the only one using Jaunty. The remote computer (the one receiving the desktop) uses Ubuntu 8.10, and is able to receive remote desktops from other computers just fine. 

And for that matter, I have Jaunty on yet another computer, and that computer is able to act as the server (i.e. sending computer) just fine. It is only the Dell M6400 described above, which when *sending* desktop info, freezes up the image on the remote side. And this very M6400, which uses Jaunty, is able to act as the remote desktop (i.e. the receiving computer) just fine.

Does it still sound to you like my problem is related with the bug you describe? If it does, I am eager to listen. But based on what you have described so far, it does not sound that way to me.

---

### Post by swarup on 2009-05-08
I have discovered who the culprit is here: it is definitely vino. That is, it is something wrong with the vino remote desktop server application on this M6400 laptop. Because I have installed another server--x11vnc--and that one is working fine. 

The problem described above only occurs when I use the default Remote Desktop software present in ubuntu. But when I use x11vnc, then I do not have any such problem.

So I'll just go on using x11vnc for now. And if anyone has any suggestion as to how to get Ubuntu's default Remote Desktop server application working, that would be great, because it is convenient to use. I did try completely uninstalling and reinstalling vino and rdesktop, but it didn't make any difference.

---

### Post by jmap82 on 2009-06-09
I wrote a short script to turn compiz off when I'm remotely viewing and back on again when I leave.  I'm no wiz at this stuff, so it may not be the best script ever, but you're welcome to use it if you want.

You can copy and paste from my wiki, [_here_]("http://script.jmap82.com/doku.php?id=jmap82sscripts:monitor").

Hope it helps :)

---

