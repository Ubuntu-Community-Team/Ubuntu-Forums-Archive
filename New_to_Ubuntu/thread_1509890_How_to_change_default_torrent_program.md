---
title: "How to change default torrent program?"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by EvCrock on 2010-06-14
I want to use Vuze, but when I downloaded a torrent from demonoid, it opened up something called "Transmission"...

...I wanna use Vuze, I'm scared of change!  This is probably a simple fix, but I'm a huge noob.

---

### Post by mikewhatever on 2010-06-14
Select 'other..' in stead of transmission, then in the file manager window that opens, point Firefox to /usr/bin/vuze.

---

### Post by EvCrock on 2010-06-14
woops, forgot to mention I'm using Chrome.  Sorry

---

### Post by Deadite81 on 2010-06-14
The easiest way to use Vuse as a system-wide default is to download a .torrent file (save it to your disk), navigate to the .torrent file in Nautilus file manager, and right click the file.
Then select "Properties", then the tab "Open With", then choose the program you would like to always open your .torrent files.  You may need to log out and back in to see the changes, but probably not.

---

### Post by EvCrock on 2010-06-14
hmm, Ubuntu wasn't on the list of programs I could use.

Well, for now I'm using Transmission, and it seems to work fine, I s'pose.  Can anyone vouch for it?  Does it work as well as Vuze?

---

### Post by Deadite81 on 2010-06-14
> hmm, Ubuntu wasn't on the list of programs I could use.Ok, call me very confused...You're looking for Vuze, not Ubuntu...

Transmission is fine, it's lightweight and simple.  IMO Deluge is much better.  Vuze, however, offers many features and is a heavy duty application.  It sounds like you don't have it installed...or do you?  I don't know what to make of your above statement.

The below instructions are going to add the "getdeb" repository, which will add the possibility to install many more applications, but they are not "official" Ubuntu packages.  I recommend it as thousands of people use it and it is good, but if you are uncomfortable with "unofficial" packages I suggest you install Vuze directly from the [Azureus home page.]("http://azureus.sourceforge.net/")[URL="http://azureus.sourceforge.net/"]
[/URL]
Learn more about [getdeb here]("http://www.getdeb.net/updates/Ubuntu/all#how_to_install").
To learn more about repositories and ppas go [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").  I recommend checking this out because it will become essential knowledge to you if you continue to use Ubuntu for any period of time and like shiny new stuff :).

To install Vuse and get updates through getdeb, open your "Start Menu" - Applications --> Accessories --> Terminal.
Once your terminal window opens paste this into it:
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo  apt-key add -
```After you enter your password this will install the secure key needed to communicate with getdeb.
In the same terminal type:
```
gksu gedit /etc/apt/sources.list
```After you enter your password your text editor will open.  Do not alter anything!  Simply put this at the **very bottom** **on its own line**:
```
deb http://archive.getdeb.net/ubuntu lucid-getdeb apps
```Save the file and close Gedit.

Now go to your "Start Menu": Administration --> Synaptic Package Manager.

Once it opens click the "Reload" button at the top left.  When it finishes search for "Azereus" or "Vuze", right click it and select "Mark For Installation".
Now click the "Apply" button in the toolbar and it will install.
Once complete you will have the menu entry: Applications --> Internet --> Vuze.

When installed Vuze *may* automatically be  made your default torrent client.  If not follow my previous post's instructions.

P.S. There is a much simpler way to do this, but the .deb link on the getdeb website seems to be broken.  Just be careful when editing anything as administrator.  If you mess something up it can have disastrous consequences if you don't know what you're doing or don't follow instructions carefully.

---

### Post by jtarin on 2010-06-14
> **EvCrock said:**
> hmm, Ubuntu wasn't on the list of programs I could use.

Possibly your in an environment other than Ubuntu.:popcorn:

---

### Post by EvCrock on 2010-06-15
> **Deadite81 said:**
> 

When installed Vuze *may* automatically be  made your default torrent client.  If not follow my previous post's instructions.

Woops, meant to write "Vuze" not Ubuntu, sorry :-P.  Also, I'd already downloaded Vuze, but went ahead and followed your instructions anyways, because I've seen "deb" stuff all over the place, so I figured why not try it out.

So then when I saved the files, I'm able to use Vuze, but it's still not set as the default torrent program.  If I have to go to the trouble of saving everything and then manually opening it with something else, then I might as well just use Transmission.  It's been working fine ever since I started this post.

I'd still like the ability to change my default torrent program, if anyone has any other solutions.  And thank you for helping a poor nooblet like myself.  I'm sure it gets old :-)

---

### Post by EvCrock on 2010-06-15
I TAKE IT BACK!!! Woops, it did actually work!!  Thank you thank you thank you!!!! Weee!!!!

---

### Post by Deadite81 on 2010-06-15
Your Welcome!

For the record, the popular program "Ubuntu Tweak" will give you a simple way to set what file type is opened with what program, along with all kinds of other configuration options very helpful to new Ubuntu users that would otherwise not know how to change these options.

If you want it you can type:
```
sudo apt-get install ubuntu-tweak
```
into a terminal or search for it in the Ubuntu Software Center or Synaptic Package Manager.

Good luck, I hope you like Ubuntu!

---

