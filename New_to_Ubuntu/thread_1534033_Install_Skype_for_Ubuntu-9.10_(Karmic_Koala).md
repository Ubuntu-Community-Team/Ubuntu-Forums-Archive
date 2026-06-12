---
title: "Install Skype for Ubuntu-9.10 (Karmic Koala)"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by Miradonis on 2010-07-18
Hello,
I'm new in Ubuntu.
What is the method of Installing **Skype** in Ubuntu-9.10 (Karmic Koala) ?

Thanks.

---

### Post by crichard on 2010-07-18
Skype is avaiable in Synaptic Package Manager,, Make sure you enabled ubuntu partner repositories...

---

### Post by Zzl1xndd on 2010-07-18
[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

### Post by owners4life5 on 2010-07-18
open a terminal.

to do this,
1)open the main menu
2)go to accessories
3)go to terminal

in the command line, type:
```
sudo apt-get install skype
```

then agree when it asks. 

when the terminal is through processing, type
```
exit
```

or just hit the exit button.

now go back to the main menu, internet, skype.

hope this helps

---

### Post by Mike_IronFist on 2010-07-18
> **Miradonis said:**
> Hello,
I'm new in Ubuntu.
What is the method of Installing **Skype** in Ubuntu-9.10 (Karmic Koala) ?

Thanks.

Hi Miradonis. Installing Skype is really, really easy, actually. Just go to this web page:
[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/")
Download Skype for "Ubuntu 8.10+32-bit". Open your Downloads folder (You can find it in the "Places" menu on the top panel), double click the skype-ubuntu-intrepid  file, and the installer should open. Put in your Ubuntu password when it tells you to, and Skype will be installed. You can then find Skype in the applications menu under "Internet".

---

### Post by Mike_IronFist on 2010-07-18
And guys, not to be preachy, but this is Absolute Beginner Talk. Shouldn't you be a bit more thorough?

> **crichard said:**
> Skype is avaiable in Synaptic Package Manager,, Make sure you enabled ubuntu partner repositories...
When I first got started with Ubuntu, I didn't even know what a repository was. Remember, we're supposed to be helping people who don't necessarily know much about Ubuntu or Linux in general. That could have used more explanation.

> **owners4life5 said:**
> open a terminal.

to do this,
1)open the main menu
2)go to accessories
3)go to terminal

in the command line, type:
```
sudo apt-get install skype
```

then agree when it asks. 

when the terminal is through processing, type
```
exit
```

or just hit the exit button.

now go back to the main menu, internet, skype.

hope this helps
First of all, Skype is not in the Ubuntu repos by default, so that's not going to work for someone who doesn't have a repo with Skype in it. Second, I don't think users should be told to use the command line when GUI programs like Synaptic work perfectly fine. I use the command line all the time, but let's not force it upon new users - it gives bad impressions.

I think both of these answers would have been perfectly fine in the "General Help" section, but I really think it's more appropriate to make things as straightforward as possible for "Absolute Beginner Talk".

---

### Post by owners4life5 on 2010-07-19
sorry...
i tried to be specific by giving directions to the prompt.
but you.re right. i shouldn.t have had that ignorance...

---

### Post by Miradonis on 2010-07-19
Hi,
I can see three softwares in the "Synaptic" when i write "Skype" in the search box.
These are: python-skype,skysentials and skytools.
But no "Skype" showing.

What now ?

Thanks everyone.

---

### Post by owners4life5 on 2010-07-19
miradonis, can you use a terminal? and if not, would you like instructions on how to get skype through it?

---

### Post by Mike_IronFist on 2010-07-19
> **Miradonis said:**
> Hi,
I can see three softwares in the "Synaptic" when i write "Skype" in the search box.
These are: python-skype,skysentials and skytools.
But no "Skype" showing.

What now ?

Thanks everyone.

Just click the link I gave you, download the 32-bit version, double-click and install it. You don't need to use Synaptic at all.

> **Mike_IronFist said:**
> Hi Miradonis. Installing Skype is really, really easy, actually. Just go to this web page:
[http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/")
Download Skype for "Ubuntu 8.10+32-bit". Open your Downloads folder (You can find it in the "Places" menu on the top panel), double click the skype-ubuntu-intrepid  file, and the installer should open. Put in your Ubuntu password when it tells you to, and Skype will be installed. You can then find Skype in the applications menu under "Internet".

---

### Post by oldsoundguy on 2010-07-19
If you can get it to work ... good luck!  Skype beta has NEVER worked in 9.10 for me.  My camera (a Logitech 9000) shows up in lsusb and works in Cheese.  The audio also tests just fine.  Skype does not see the camera or something stupid like that.  As it does not turn on.

---

### Post by crichard on 2010-07-19
> **Miradonis said:**
> Hi,
I can see three softwares in the "Synaptic" when i write "Skype" in the search box.
These are: python-skype,skysentials and skytools.
But no "Skype" showing.

What now ?

Thanks everyone.

As I told you earlier, you've to enable ubuntu partner repo, to install skype. Goto System-> Administration->Software Sources

Enter you password to make changes on sourcelist

Goto other software tab and enable(check box should be checked) **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner** & Press Close button.

Then click Reload button, to update your sourcelist.

Then, folow this command on terminal,
 
```
sudo apt-get install skype
```

or 
Goto, Synaptic Package Manager & find skype package to install it.

---

### Post by Miradonis on 2010-07-19
Hello,
Thanks everyone.
I successfully install Skype by downloading it from the link: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/)

---

### Post by oldsoundguy on 2010-07-19
Removed skype beta and tried the synaptic install. (for Lucid).  Still dead in the water.
camera and microphone do not turn on.  Does not access the ISP.

---

### Post by kNoksas on 2010-12-28
Sorry if I'm posting not in the right place but I have a problem, I had downloaded skype from official site. I tried to install 64-bit but it even won't let me. So I downloaded 32-bit and when I push a button install I get this:
Help me to get a password, thanks. :)
[[IMG]http://img43.imageshack.us/img43/8387/screenshotgn.png[/IMG]]("http://img43.imageshack.us/i/screenshotgn.png/")

---

### Post by madjr on 2010-12-28
> **kNoksas said:**
> Sorry if I'm posting not in the right place but I have a problem, I had downloaded skype from official site. I tried to install 64-bit but it even won't let me. So I downloaded 32-bit and when I push a button install I get this:
Help me to get a password, thanks. :)
[[IMG]http://img43.imageshack.us/img43/8387/screenshotgn.png[/IMG]]("http://img43.imageshack.us/i/screenshotgn.png/")

you need to enter your **ubuntu user password**.

but, if you're not the owner then tell him/her to enter it.

---

### Post by kNoksas on 2010-12-28
Thanks, but I forget that password too. :D

---

