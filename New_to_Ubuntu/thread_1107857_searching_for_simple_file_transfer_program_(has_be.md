---
title: "searching for simple file transfer program (has been posted before)"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by darthmob on 2009-03-27
I'm looking for a simple file transfer program which I think was posted here on the forums. some things I do remember about it:

[list]
[*]it was a contribution for some sort of competition
[*]it was presented in a video; two guys with two computers transfered files between those and talked about how simple it was
[*]it had a simple gui with a list of clients where you could drag and drop files to transfer them
[/list]

does anyone know what I am talking about?

---

### Post by finer recliner on 2009-03-27
i dont know what you're referring to, but i thought i would recommend filezilla anyways

---

### Post by darthmob on 2009-03-27
filezilla is a ftp client. I'm looking for a program that allows simple peer-to-peer transfers without having to set up a ftp or shared folders. :)

---

### Post by clive littlewood on 2009-03-27
Hi

The program you are refering to is i think Giver.

A video of the program was on youtube.

The app is in synaptic (just search giver)

I will add that although giver is a great little app i believe that no further developement is being done.

Add profile photos and a couple of other things were buggy when i tried it.  :(

Hope this helps

Clive

---

### Post by darthmob on 2009-03-27
yes that is what I was looking for! it's fine for me as long as the transfer works.

last release was in 2007 but there seems to be some activity on the [google.code-page]("http://code.google.com/p/giver/updates/list").

---

### Post by clive littlewood on 2009-03-27
Hi

Yes a good little app not well publicised.

I think the video is waaaaaaaaaaaaaaaaaay over the top  :lolflag:

Glad you found it.

Clive

---

### Post by VCoolio on 2009-03-27
You can also take a look at woof. Maybe you know the gnome-do plugin for it. The app itself is somewhere on the web. It is commandline though, although I put a slightly modified version with a nautilusscript on gnome-look.org (search for woofgui). We are busy developing a full gui-front end for it. 
The app works like this: you command "woof filename" and it echoes a link (ipaddress: port) that you can give to the one you want to share the file to. He can then get the file from his browser. Advantages: receivers do not need to be on the same network or have giver or even run linux, all they need is a browser.

---

### Post by Nepherte on 2009-03-27
While looking at the svn repository of giver, they seem to continue to work on it. Their last commit dates of 19 March 2009 so perhaps you should use the svn version.

---

### Post by HermanAB on 2009-03-27
By the way, installing FTP is trivial and proftp or vsftp work out of the box - you just install it using synaptic and it works.  On the client side, you can use Nautilus, Konqueror, FileZilla, Gftp or a zoo of others.  On Gnome (Ubuntu) I use Nautilus, on KDE (Mandriva) I use Konqueror and on Windows I use FileZilla - click-drag-drop - nothing to it.

---

### Post by darthmob on 2009-03-27
> **clive littlewood said:**
> I think the video is waaaaaaaaaaaaaaaaaay over the top  :lolflag:it is a bit like teleshopping on tv but it sticked to my mind! ;)

> **VCoolio said:**
> You can also take a look at woof. Maybe you know the gnome-do plugin for it. The app itself is somewhere on the web. It is commandline though, although I put a slightly modified version with a nautilusscript on gnome-look.org (search for woofgui).thanks a lot for the hint! somewhere on the web is [here]("http://www.home.unix-ag.org/simon/woof.html") and [here]("http://www.gnome-look.org/content/show.php/Woof_ui?content=100441") btw. I do really like it as it works simple with your gui, you don't have to run the program in the background, you can send files to pc's running windows and it is supported by gnome-do (which has to be one of my favorite applications on ubuntu). I'm not sure though how you specify a certain file when you use gnome-do. do you know how it works?

> **Nepherte said:**
> While looking at the svn repository of giver, they seem to continue to work on it. Their last commit dates of 19 March 2009 so perhaps you should use the svn version.you are right but I'm too lazy to properly compile software. it works the way it is and that's enough for me. :)

> **HermanAB said:**
> By the way, installing FTP is trivial and proftp or vsftp work out of the box - you just install it using synaptic and it works.  On the client side, you can use Nautilus, Konqueror, FileZilla, Gftp or a zoo of others.  On Gnome (Ubuntu) I use Nautilus, on KDE (Mandriva) I use Konqueror and on Windows I use FileZilla - click-drag-drop - nothing to it.the thing is I want something that is fast and simple and does not rely on a client-server model. for example I might want to transfer files from my laptop to my desktop or the other way round. I don't want to set up a ftp server on both of them. with giver you just have the program running with drag drop functionality and woof works even from the context menu and does require no background program at all. it can't be much more trivial than that! :)

---

### Post by VCoolio on 2009-03-27
For gnome-do plugin: make sure the gnome-do woof plugin is installed (it is somewhere in third party plugins) and then just first find your file, then select woof and third select chat-buddy. Drawback here is that both you and receiver must have chatclient running and be buddies.

---

### Post by darthmob on 2009-03-27
the problem was that I had not the advanced folders / files handling plugin installed. I was not able to browse for files in gnome-do which confused me.

the second problem seems to be a [bug]("https://bugs.launchpad.net/do-plugins/+bug/276011") with the plugin. I guess it's only a matter of time until it is fixed.

---

### Post by mxboy15u on 2009-05-01
Giver does nothing for me when I try to send a file, is there supposed to be some sort of confirmation that asks if I want to accept it or where to save it?

---

### Post by HermanAB on 2009-05-01
Hmm, every self respecting Linux system should have SSH server installed, so transferring files between Linux machines is trivial by default. The fly in the ointment is Windows.  That is why I suggest Filezilla.

---

