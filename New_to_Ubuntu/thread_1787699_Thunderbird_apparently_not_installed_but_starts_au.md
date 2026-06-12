---
title: "Thunderbird apparently not installed but starts automatically after boot"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by KarenAK on 2011-06-21
After updating to 11.04 something's wrong with my Thunderbird installation.
When I turn on the laptop Firefox and Thunderbird start automatically as they have always done.
But
Now I have closed Thunderbird accidentally and wanted to restart it, and Ubuntu tells me it's not installed !
In the Synaptic Package Manager I can mark it for installation but I worry about the Lightning (?) add-on. Don't want to lose my calendar ! And neither the mail of course !

So I decided to ask first before doing anything dumb.

So my question is: Is it ok to simply reinstall Thunderbird ? What about the calendar ? The Package Manager doesn't say anything about Lightning...

Or is there something nice and easy I can do in the home folder that will tell Ubuntu that it IS already installed ?

I'd much appreciate any help.
Thanks in advance.

---

### Post by Rex Bouwense on 2011-06-21
Before you do anything drastic, have you just tried rebooting to see if it will start automatically?

---

### Post by dFlyer on 2011-06-21
It should be ok to reinstall thunderbird, but I would back everything up to be safe. I don't use thunderbird, I use evolution and have in the past marked it for reinstall and still had my calendar and past email.

---

### Post by KarenAK on 2011-06-21
it always starts when I turn on the comp - only since I never accidentally closed it before, I didn't realize until now that it is not recognized as being already installed. 
I could of course reboot the comp every time I accidentally quit Thunderbird but I assume that there's a way to fix this and maybe somebody can explain why it happened

---

### Post by philinux on 2011-06-21
Karenak

Open a terminal from accessories apps.

Type in thunderbird and post back anything it spits out.

---

### Post by KarenAK on 2011-06-21
The program 'thunderbird' is currently not installed.  You can install it by typing:
sudo apt-get install thunderbird



I might also add that there is .mozilla-thunderbird folder in in my home folder.

---

### Post by jtarin on 2011-06-21
> **KarenAK said:**
> The program 'thunderbird' is currently not installed.  You can install it by typing:
sudo apt-get install thunderbird



I might also add that there is .mozilla-thunderbird folder in in my home folder.That's the folder you want to back up.Once done....reinstall.

---

### Post by disabled20191128 on 2011-06-21
You said that there was a  .mozilla-thunderbird folder, why don't you search for your data in it (calendar...) and make a backup?

---

### Post by smurphy_it on 2011-06-21
Did you try searching for it.  Perhaps the package manager doesn't see it as installed, even though it is.

```
which thunderbird
```
if that fails:
```
sudo find / -name thunderbird
```

If you find the binary and you can execute it, then just create a symbolic link to it, or create a menu entry for it.  If the binary isn't in your "path" then just edit your path variable, or copy it to somewhere within your existing path.

---

### Post by KarenAK on 2011-06-21
I did backup that folder. That is not my question.

My questions are: 

If I reinstall Thunderbird, will it recognize that folder and will it recognize the lightning add-on. Will it use the existing configuration / preferences / data ?

Somehow Thunderbird is still in the autostart and runs perfectly - will it continue to do so  after I install or will that installation overwrite everything with default settings.

---

### Post by KarenAK on 2011-06-21
ok - I just checked in Startup Applications for the command it uses and copied that into the terminal window - started it just fine.

Now: 
1) - how do I tell Ubuntu that the application is right there ?
2) - failing that, how do I create that link ?

---

### Post by jtarin on 2011-06-21
Let me ask a question.....What method did you use to install Thunderbird?

---

### Post by KarenAK on 2011-06-21
I am sorry - that was 2 years ago. I don't remember. But since I have never been very comfortable with using the Terminal, I assume that it probably was the Software Center. But it might have been the Synaptic Package Manager. 
So far i never had any trouble with Thunderbird when I updated Ubuntu. It was always just there..... Sorry.

---

### Post by jtarin on 2011-06-21
Ubuntu knows it's there......it has been installed in the PATH that Ubuntu looks when starting applications.99% of your applications can be started from the terminal with just the application name. You can normally make a link to the executable using an icon on your desktop by simply using the application name in the command.

---

### Post by amanchesterman on 2011-06-22
Hi, this is to try to answer the question you asked earlier but (I think) didn't get answered:
*If I reinstall Thunderbird, will it recognize that folder and will it recognize the lightning add-on. Will it use the existing configuration / preferences / data ?*

If you install Thunderbird it will automatically create a new 'profile'. On my laptop, running Ubuntu 10.10, the profile is in the .thunderbird folder in my home folder -- not '.mozilla-thunderbird' as on yours, but maybe that is because you have a different version of Ubuntu or Thunderbird.

The profile appears as a folder within that folder and is called 'xxxxxxxxx.default', where 'xxxxxxxxx' is an arbitrary string of letters and numbers.

Your profile contains all your Thunderbird settings, emails and addresses, as well as calendar events and tasks if you use Lightning. So what you would need to do is:
a) backup your existing profile
b) install Thunderbird with the Lightning add-on
c) delete the newly-created profile, having first noted the 'xxxxxxxx' string
d) copy your saved profile into the .mozilla-thunderbird folder and rename it 'xxxxxxxx.default' (i.e. give it the name of the empty, newly-created profile you have just deleted).

I did this when I transferred all my Thunderbird + Lightning data from a Windows laptop to my Ubuntu machine, and it worked perfectly.

I'm sorry that I can't help you with your questions about why Ubuntu doesn't recognise Thunderbird as being installed, or whether it would automatically start when you turn on your computer, I haven't been using Ubuntu very long and I am still quite new to it.

Good wishes
John

---

### Post by KarenAK on 2011-06-23
Um, should have waited a while longer for that post, I guess.

Thunderbird is installed now and shows my mail but all account settings and the calendar are gone.... If I knew in which file that info is stored, I could probably recover it.

---

### Post by Rex Bouwense on 2011-06-23
Your calender data should be stored (as a hidden file) in
.mozilla-thunderbird
The file I believe is called calendar-data.

---

