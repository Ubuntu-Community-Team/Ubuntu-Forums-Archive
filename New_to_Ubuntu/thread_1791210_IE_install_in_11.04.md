---
title: "IE install in 11.04 ?"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by iansane on 2011-06-26
Hi,

Has anyone successfully installed Internet Explorer of any version in wine on 11.04? Or even 10.04-10.10 ?

ies4linux does not work.

I read somewhere that it was due to a change in wine and how the install script tries to create a wineprefix which is not allowed in this way any more.

I also get a warning telling me that wine is old and I should install 0.9.x or higher. This is funny since I've got 1.3 installed. The script is obviously way outdated so I'm wondering if anyone knows of a new way to install IE in wine.

Thanks

---

### Post by Sylslay on 2011-06-26
I try be kind?

What for?

IE on linux?

---

### Post by Enigmapond on 2011-06-26
> **Sylslay said:**
> I try be kind?

What for?

IE on linux?

+1...Why, on earth, for? It runs slow in Linux and there are so many other browsers native to linux that work 100x's better.

---

### Post by robertc36 on 2011-06-26
use winetricks or playonlinux. It install version 7.

---

### Post by iansane on 2011-06-26
> **Enigmapond said:**
> +1...Why, on earth, for? It runs slow in Linux and there are so many other browsers native to linux that work 100x's better.

LOL agreed but I'm an aspiring web developer and need to test out web sites on IE since the M$ monster has most business and average users (at least in my area) using IE. It's amazing how many people say "what's a firefox or a chrome?"

> robertc36 	
Re: IE install in 11.04 ?
use winetricks or playonlinux. It install version 7. 


Thanks, I just recently heard of winetricks and have not tried it out to see what it is and what it's for so I wasn't aware. 7 is great. Now I'll need to try and get IE8 too, or if 7 works I can install the developer tool bar on it maybe and use that to test for IE6 - 8

---

### Post by iansane on 2011-06-26
Awesome! If it works, I had to figure out how because the option to install an app didn't include any IE at all.

I'll list the steps for anyone else after it finishes downloading and installing IE 6 - 8 if it works.

Well ok so it won't allow me to install them all like I was hoping. Maybe if I do each one individually.

Steps to get IE8 were:

1. open winetricks
2. choose the option, "Select the default wine prefix" (confusing to me since I don't know what a prefix is and it sounds like I'm doing something that will be the default for everything in wine)
3. click "OK"
4. choose option, "Install a Windows DLL or component"
5. click "OK"
6. Now choose IE6, 7, or 8 from the list and check the checkbox
7. click "OK"

Now this is where I got confused and had a ton of popups so can't really explain the steps.

First mistake I made was choosing all 3 versions at once.

Basically it downloaded all the files needed including the IE stand alone installer and installed it for me. The problem was that it did each one in order and wanted to restart the computer which actually restarted wine and opened some graphical server window which I know nothing about. There was a prompt for user name and password to connect to some server which fails because my Ubuntu user name and password don't work for it. But I just closed the window and it continued the install process. 

In the end, I ended up with IE8 only and it works but gives me that familiar "sorry IE encountered an error and needs to close" popup but when I click OK IE does not close and continues working fine.

Oh well, this is definate progress.

Thanks

---

### Post by Sylslay on 2011-06-26
You can Install Window XP in Virtual Box.

to check out IE browser wroks correctly with Yours apps.

And after trial... delete all VirtualMachine.

BTW: Opera Browsers can act as IE  and is in linux repo.

---

### Post by mikenev on 2011-06-26
I also recommend using a virtualbox install.

As a web developer, I tried to use IE under winetricks and found that it didn't work quite the same as actual IE running in windows. Fairly often it would mess up the fonts or the display. So when I thought I had my apps working alright, my users would see something totally different.

---

### Post by iansane on 2011-06-26
> **mikenev said:**
> I also recommend using a virtualbox install.

As a web developer, I tried to use IE under winetricks and found that it didn't work quite the same as actual IE running in windows. Fairly often it would mess up the fonts or the display. So when I thought I had my apps working alright, my users would see something totally different.

Thanks, that's good info to know. I was also trying to install the IEdevtoolbar in IE and finally got it there but it's missing IE6. Also with so many other issues I had trying to install fonts, dot net framework, windows installer, .... nothing is working. Either it says I need windows installer 3.0 or it says msiexec.exe has encounterd a serious issue and needs to close. I've decided this is way too much trouble. Also have to use windows to get through photoshop psd site layouts so I'm just going to use VirtualBox on Ubuntu partition and virtualPC with ubuntu installed on my win7 partition so I can get the best of both worlds no matter which one I boot too.

Thanks all for the suggestions and info :-)

---

### Post by bobbins on 2011-06-26
If you are running Chrome or Firefox you can find IE tab extensions that render as IE.

---

### Post by mastablasta on 2011-06-27
> **bobbins said:**
> If you are running Chrome or Firefox you can find IE tab extensions that render as IE.
 
 
.net is still not going to work there.
 
so either dual boot or virtualization.

---

### Post by iansane on 2011-06-27
> **mastablasta said:**
> .net is still not going to work there.
 
so either dual boot or virtualization.

Yeah there's too many unknowns really. I don't think I would really need dot net since my apps are all html, css, and php (no asp.net). But I need to feel 100% confident that I've tested the css in IE 6 - 8 and would not want to think it all works and find out afterward that something doesn't' actually render correctly in IE from a windows machine.

So the VM with actual windows and IE is probably the best bet even if I could get it to work in wine. Just to be 100% certain.

I've been working on setting up firefox and chrome with all the web dev tools for optimum coding so I can still do the development on Ubuntu and just have the VM open to IE with IEdevtoolbar and have it using a minimal amount of RAM and CPU. No big deal in other words, just another window open :-)

---

### Post by MARP1961 on 2011-06-27
I wouldn't use Internet Explorer even in Windows! Both Firefox and Chrome are so much more straightforward and quick.

---

### Post by mkornig on 2011-06-27
> **Sylslay said:**
> 
BTW: Opera Browsers can act as IE  and is in linux repo.

Interesting. Which IE version? I'll check it out.

---

### Post by Sylslay on 2011-06-27
I had Opera Instaled on Fedora, 
don't know witch IE version, at the moment:

In Firefox You can change options:

about:config, 
and tune...

---

