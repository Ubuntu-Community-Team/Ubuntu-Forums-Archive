---
title: "Launchpad Registration problem"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by Tony.B on 2009-09-20
I am very, very new to Ubuntu. I'm also a great deal older (but, alas, not wiser) than all you computer whizz kids; I'm very much out of my comfort zone, but learning so much, and I've encountered a problem which I hope someone will be kind enough to solve:

I've tried to register on Launchpad, but every time I enter my email address I get the response that I've already registered.
Now, I know that I haven't already registered, but I nevertheless checked my email for some sort of confirmation.  Of course there was nothing there.
Then I had a bright idea... I entered my email address again, but this time in the "forgotten password" section, in the hope that the Launchpad people would be able to furnish me with the missing information. Guess what? I got a reply saying that my email address wasn't registered.

I'm a bit perplexed. Can anyone please suggest a solution?

Thanks in advance

---

### Post by baltadt on 2009-09-20
I have no idea what it could be.  Although go on xchat (applications, internet, xchat). login and connect to #launchpad server and the people in there should be able to help you.

---

### Post by Tony.B on 2009-09-20
Thanks very much for that suggestion.
Unfortunately, though, it won't work.
If I go to *Applications > Internet*, my system doesn't give me the option *X-Chat*.
But thanks for the idea.

---

### Post by Tony.B on 2009-09-21
Well, I don't know quite what happened, but everything seems ok now.
My computer still insisted that I've already registered, but I found another link on the *Edit Profile* page which allowed me to set up a new password.

---

### Post by swoody on 2009-09-21
TonyB. - Hello, and welcome to Ubuntu and the Forums ):P

IRC is a **great** resource for asking questions, and getting help. However, xchat does not come pre-installed in Ubuntu. To install it, simply open a terminal (Applications>Accessories>Terminal) and type in:
```
sudo apt-get install xchat
```
It will ask you for your password. Simply type it in, and press 'Enter'. If you're not familiar with the terminal, please make a note: when typing in your password to the terminal, it will act as if you are typing nothing in. This is normal, but do remember that it is actually setup to work this way for security purposes. Once installation has completed, you can proceed to Applications>Internet>xchat to open the program.

For more info about setting up your IRC client, please see the links in my signature.

As you also mentioned that you are new to Ubuntu, and trying to learn as much as you can about it, you may want to download a copy of the [FREE Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/download_main.html") It's a great learning tool, and a great reference to have on hand :)

---

### Post by zkriesse on 2009-09-21
Tony B. First a big welcome to the forums. Second, if you would like to use Xchat you can either use this command in the terminal. 
```
sudo apt-get install xchat
```
Or you can go to Applications/Add/Remove, and do this. The first screenshot is what you will see when clicking Applications Add/Remove, click the drop-down box and choose All Available Applications. Then in the search box type Xchat. It will bring up three options. Check the first one then click apply at the bottom. Accept the install then when it's done Xchat will be in Applications/Internet/Xchat. That's It! If you need help on joining a channel you can ask me or Swoody for help.

---

### Post by Tony.B on 2009-09-21
[FONT="Tahoma"]Hi Swoody & Zachk18,
Thank you for your responses. I had to look up the term *IRC* which I've not come across before.
The idea of typing in some sort of code is a bit terrifying as I'm not at all computer-literate (and therefore scared about making a mistake) so I probably won't do this immediately.
In the meantime, however, I've downloaded the *Ubuntu Pocket Guide* and will attempt to memorise every word.
Thank you once again for the help.[/FONT]

---

### Post by swoody on 2009-09-21
Ah, well that's ok, TonyB. We were all completly new to Ubuntu/Linux at one point or another, and the command line can be a bit intimidating at first. Just know that it is your friend, and is there to assist you with operating your computer. The command "sudo apt-get install xchat" is a very simple command that only installs the program 'xchat' on your computer.

```
sudo
```
Simply runs the command with 'sudo' privelages. You can think about this the same as the 'Admin' account in Windows.
```
apt-get
```
is a program that deals with installing/removing packages on your computer.
```
install
```
Just tells the program 'apt-get' that you want it to install some package.
```
xchat
```
Simply tells 'apt-get' that this is the package you want it to install.

As you can see from above, commands can be broken down into their simpler parts. They all work together to acheive the result that you are trying to get. For some more in-depth reading to familiarize you with the command line, here's a couple links you should check out:

[Using the Terminal]("https://help.ubuntu.com/community/UsingTheTerminal")
[Commandline How-to]("https://help.ubuntu.com/community/CommandlineHowto")

Also, there should be a nice big section on the Terminal/Command Line in the Pocket Guide you downloaded. They are all great resources to read through, and I'm sure you'll be able to learn quite a bit from them :)

If you're still going to hold off before you delve into the terminal, there is a program installed by default - Pidgin - that handles IRC as well. You can find Pidgin under Applications>Internet>Pidgin. Then you simply go through the setup prompts it gives you, and you can create an IRC account to log onto IRC channels with.

---

### Post by Tony.B on 2009-09-22
Thank you, Swoody, for explaining that so brilliantly.

Nervously I entered *sudo apt-get install xchat* and, amazingly I didn't end up with my biggest nightmare: a black screen with nothing except a persistent flashing cursor. 
 
I haven't had a chance to look at *xchat* yet - too busy reading the *Ubuntu Pocket Guide*, but I think in the meantime we can mark this item (do you call it a *thread*?) as closed, though I haven't found out how to do that yet.

Thank you once again for your help, MUCH appreciated.

---

### Post by swoody on 2009-09-22
Well, I'm very glad to hear that your first adventure into the command line was successful :D

Have fun learning with IRC, and remember, if you have any questions, feel free to join **#ubuntu-beginners-help** or **#ubuntu** on the FreeNode network.

Also, yes, this is a 'thread' and you can mark it [SOLVED] by going to the far top-right of this page, clicking on 'Thread Tools' and then mark as solved. Hope that helps you out :)

---

### Post by Flimm on 2009-09-22
EDIT: deleted because I decided it was too much like [flame-bait](http://en.wikipedia.org/wiki/Flamebait).

---

