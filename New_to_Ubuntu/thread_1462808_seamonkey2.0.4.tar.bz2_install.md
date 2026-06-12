---
title: "seamonkey2.0.4.tar.bz2 install"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-04-26
OK, you're dealing with 62 YOM that's had a head injury. I am looking at using the Seamonkey browser, downloaded it, and have it waiting in the downloads file. I've looked at several references but didn't find anything really easy to follow on how to proceed from here.

Would anybody have a lay person step-by-step direction for getting it from tar format (?) to usable and how to install it to operate like the Firefox does? (easy updates, etc)

Thanks for the patience it takes and dealing with a real bottom rung computer user.:confused:

---

### Post by arochester on 2010-04-26
57 YOM that's had a head injury (brain haemorrhage) here. Try installing it through Ubuntuzilla - [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by flyfishingphil on 2010-04-26
Tried adding the repository shown by doing a copy/paste. Here's what I get back:

No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found

That's why I asked if anybody had step-by-step. Figure there is something else there I need to do but am unfamiliar with "programming" so I'm at ground 0 when it comes to this.

---

### Post by user1397 on 2010-04-26
You should always try to install using the default ubuntu repositories if you can (it is easier, safer, and guaranteed to work)

You could just go to the software center, or synaptic package manager and search for seamonkey and install it that way.

Installing from source (like the link you provided) is your last resort.

Also, this is not even close to anything that could be considered 'programming,' so keep in mind that it is not that hard and you'll get it eventually, albeit probably with a bit of help and a bit of patience.

---

### Post by arochester on 2010-04-26
I think you have Copied and Pasted the top line. 

Run the bottom line (that begins echo - etc) in a Terminal. That will automatically add the repository to your sources list.

Remember to get the key (lower down the page) (the line that begins sudo apt-key adv etc) before you update

---

### Post by flyfishingphil on 2010-04-26
I went thru the Ubuntu Software Center to get Seamonkey but it's an older version that no longer is supported. As soon as you download it recommends that you go to the Ubuntuzilla site and get the version listed above. That's where it gets to be fun. Now that I've downloaded it how the devil do I get it installed and working?

Well, I just noticed it's a little after 3 and I really should get some sleep. I'll try this again later this morning after I "rise and shine". Maybe I can figure it out then. Thanks for the assists and I'll check it again later.

---

### Post by soloman498 on 2010-04-26
Here is a site that shows you how to unpack different files...  [http://wiki.linuxquestions.org/wiki/Unpack](http://wiki.linuxquestions.org/wiki/Unpack)

---

### Post by 3rdalbum on 2010-04-26
Just copy and paste each of these lines into the terminal. This information is on the site linked by Arochester:

```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
sudo apt-get update
sudo apt-get install seamonkey-mozilla-build
```

There is [an entirely GUI way of doing it]("http://www.psychocats.net/ubuntu/ubuntuzilla"), but it's actually more complicated.

What you will have just done is add the Ubuntuzilla repository to your package manager - this lets your package manager look at and install software from the Ubuntuzilla website. It adds a key file, so it can be sure that the packages haven't been tampered with in transit. It gets a list of what packages are available, and then finally it installs Seamonkey from Ubuntuzilla.

---

### Post by flyfishingphil on 2010-04-26
OK. After I went to bed, and before I went to sleep, my thoughts were in regards to Synaptic and whether or not Seamonkey was there. I just checked and it was, so I clicked on that and clicked on the install process. It downloaded, etc, but I can't find it anywhere in the Applications list. I went back and checked and it shows:
[I]
seamonkey-mozilla-build  2.0.4-0ubuntu1[/I] with the green installed box to the left

What am I missing on getting it available to use? Where is it?

(Surprising how much fog one can be in on a sunny, breezy day, isn't it?)

Call it Solved. I give up. Problems encountered include the call by several sites that the java in Seamonkey be updated. It's already been installed but Seamonkey doesn't seem to recognize that, doesn't provide an easy method for connecting the two and doesn't seem to be much different from Firefox. Guess I'll just stay with FF and call it good.

---

