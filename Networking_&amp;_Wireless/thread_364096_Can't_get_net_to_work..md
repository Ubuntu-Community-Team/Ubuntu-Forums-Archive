---
title: "Can't get net to work."
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by Ashkwil on 2007-02-17
Ive just installed ubutu on my other PC and ive plugged it into my Broadband modem with bot USB and Ethernet and it has no reponse it shows no messages saying anything has been plugged in and i dont understand the Netowrking window.

How can i get my net working?

Ash~

---

### Post by Ashkwil on 2007-02-17
Sorry for the bump but i have to go to bed soon any help is really appreciated!

---

### Post by gradedcheese on 2007-02-17
So this modem lets you connect via either USB or Ethernet?  And then it has a separate plug for the DSL phone line or whatever?

If so, disconenct the USB and just connect the Ethernet.  Then you'll need to find how to configure the modem settings (PPPoE, specifically).  There are some guides here (search for 'ADSL modem') that will work.  Personally, I don't like PPPoE and DSL modems.  What I'd to is buy a simple cheapo "home networking" router at the store ($50?) and plug that in between the modem and your PC.  Then configure it using the instructions that it comes with.  You'll now have a real always-on LAN connection, like you would at an office.  No more ADSL modem stuff to deal with.  Either way, I'm pretty sure it can be made to work.

---

### Post by Ashkwil on 2007-02-17
I have it plugged in via ethernet i am going to buy a router when i can afford it. i need to know how to configure it as i am totally new to linux

Ash~

---

### Post by gradedcheese on 2007-02-17
Ok.  Here's a guide for getting PPPoE working (essentially that's what you need for ADSL modems)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29)

I hope that helps.  Do switch to a router as soon as you can :)

---

### Post by Ashkwil on 2007-02-17
How to install Broadband ADSL/PPPoE Client (RP-PPPoE) 

Read #General Notes 
Read #How to install Basic Compilers (build-essential) 

wget -c [http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/files/download/rp-pppoe-3.8.tar.gz)
sudo tar zxvf rp-pppoe-3.8.tar.gz -C /opt/
sudo chown -R root:root /opt/rp-pppoe-3.8/
gksudo gedit /usr/share/applications/RP-PPPoE.desktop

Insert the following lines into the new file 

[Desktop Entry]
Name=RP-PPPoE
Comment=RP-PPPoE
Exec=gksudo /opt/rp-pppoe-3.8/go-gui
Icon=pppoeconf.xpm
Terminal=false
Type=Application
Categories=Application;Network;

Save the edited file 

Applications -> Internet -> RP-PPPoE 


Thats what it says and i dont have a clue what its talking about.

---

### Post by gradedcheese on 2007-02-17
Did you read 'general notes' like it said?

Open the terminal (in Gnome it's Applications->Accessories->Terminal, in your Kubuntu it's somewhere too).  Now when you see them tell you to do something, you type (or paste) it in and press Enter.

---

### Post by Ashkwil on 2007-02-18
Ok ive got the tar file on the other computer can you please kind of in your own words tell me what to do from there i am a real "n00b" if you will to linux i really appreciate the help!

Ash~:(

---

### Post by Ashkwil on 2007-02-18
Sorry to bump this early but it went wuite far down the list.

---

### Post by gradedcheese on 2007-02-18
Ok.  Now that you have the file... where is it?  Move it to your "home" directory (Places->Home Folder) on the computer you want to get this working on.  You can use a USB disk or whatever else to transfer it.

Now open Applications->Accessories->Terminal, this is the shell.  You can paste in (or type) a command and, to run it, press "enter".   Try "list directory", type "ls" and press enter: that will show you the files in your home directory.  Ok so far?  Now paste in:

sudo tar zxvf rp-pppoe-3.8.tar.gz -C /opt/

and press Enter to run it.  This extracts the file (which is an archive) into /opt/  Similarly, run the next commands in the guide.  The last one (gedit) just opens a text file in an editor, and lets you make changes to it.

---

### Post by Ashkwil on 2007-02-18
so after ive done this i should just be able to open firefox and surf the web?

Ash~

---

### Post by Ashkwil on 2007-02-18
Ok i did it and now have a file in Applications > Internet > RP-PPPoE

When i click ti nothing happends though. it asks for my password and then nothing.

whats wrong?

---

### Post by Ashkwil on 2007-02-18
Can anyone help?

---

### Post by Ashkwil on 2007-02-18
Bump

---

### Post by gradedcheese on 2007-02-18
try running this in a terminal:

```

gksudo /opt/rp-pppoe-3.8/go-gui

```

after it gets your password, what happens?  Any errors shown in the terminal?

---

### Post by Ashkwil on 2007-02-18
Yes i just ran it and got this error.

```
Checking for C compiler default output file name... see `config.log` for more details.
Oops!  It looks like .configure failed.
```

Any idea?

Also do you have MSN it may be easier to talk to you seen as you sound like you knw your stuff ;) if not or dont want to give no matter we can do it on here.

Thanks for the help so far

Ash~

---

### Post by gradedcheese on 2007-02-18
when you were reading the guide, did you follow their instructions about installing build-essential?  It said "# Read #How to install Basic Compilers (build-essential) "  ...if you did not do this, then open a terminal and run:

sudo apt-get install build-essential

...now after that's done, do the previous step (or use that icon) again.  And no, I do not have MSN.  I don't have MS-anything...

---

### Post by Ashkwil on 2007-02-18
i did that then tooka screenie of the code but when i make the jpg n put it on my flash drive it doesnt show on my windows computer...

anyway i get this.

After the install build

Reading package list... Done
Building dependancy tree
Reading state information.. Done
E: Couldnt find package build

After doing gksudo thing.

Running ./configure...
Checking for gcc... gcc
Checking for C compiler default output file name... configure: error: C compiler
cannot create executonables
See `config.log` for more details.
Oops! It looks like ./configure failed.

Sorry if i did any typos i typed ti as fast as i could lol...

Also a question why can i dont open up .txt i make on ubuntu on windows? but i can oprn up .txt i make on windows on ubuntu?

Ash~

---

### Post by gradedcheese on 2007-02-18
it's **build-essential** not 'build':

```

sudo apt-get install build-essential

```

...and text is text.  the OS doesn't matter, so yes Windows text files will work in Linux.  Linux text files will work in Windows, but use 'wordpad' rather than 'notepad' to view them.

---

### Post by Ashkwil on 2007-02-18
yes i did build-essential i was just saying build as short forum and thats what heppend... so do you have no idea?

also the files dont even SHOW when i open my flashdrive i cant even attempt to open them.

---

### Post by gradedcheese on 2007-02-18
Do you have extra repositories enabled (yes, that was also in their instructions!).  There are GUI ways, but here's what I do:

```

sudo gedit /etc/apt/sources.list

```

now, see the lines starting with '#'?  Remove the '#' to uncomment-them.  Now save and close gedit.  Now:

```

sudo apt-get update
sudo apt-get install build-essential

```

As for the text files... copy a file onto the flash drive in Ubuntu.  Right-click the flash drive's icon and choose 'eject', now wait until the progress bar is done.  Unplug the drive and plug it into the Windows PC.  I bet you do see the files then?

---

### Post by Ashkwil on 2007-02-18
ok i took out all of the #'s and then ran the first command. do i run both lines SEPERATE? or both at same time together?

I ran them seperate and got this.(well theres was AY too much but at the bottom of the update i got this.)

W: Some index files failed to download, they have bee ignored, or old ones used instead.

The build essential one said:

Reading package lists... Done
Building dependancy tree
Reading state information...Done
E: couldnt find package build-essential

Lol it feels like im going round in circles!

Thanks for being the only person trying to help me though lol.

Ash~

---

