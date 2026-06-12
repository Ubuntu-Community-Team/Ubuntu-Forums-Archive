---
title: "[SOLVED] Setting up File sharing between two Ubuntu Gutsy 7.10 computers"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by gw4k on 2008-03-24
Hello everyone!

I first want to thank you all for your help.  This forum has been a real godsend!  Not only have I been able to ditch windows (for the most part...Gaming is still a must under Windows).  Not only that but i have been able to install Ubuntu on my Toshiba laptop....

Not an easy task but with all the help I have found here, I have been able to do amazing things.

So thanks everyone.

Alright friends, I am working on setting up a network between my Laptop and my desktop.  Both are running Ubuntu Gutsy 7.10.

Basically my friends, I have done this for both computers.

I have gone into the folder shared option under system.  I have installed both the NFS and the Samba on both computers.  I have gone into the options and selected the locations that I want to share.  I then went into the terminal (on both machines) and reloaded the Samba program.

sudo -i
/etc/inti.d/samba reload

Everything went ok.

I then set the password for Samba on both systems

Now when I go into the places options and select network.  It then shows my Desktop, my Laptop and the  Windows Network.

No matter which I click on from any computer I receive this message.

Sorry, couldn't display all the contents of "Windows Network: lukepmiller-des".

My friends, I am at a loss.  If anyone can help me set up folder sharing that would be awesome.  Thanks again Linux brothers/sisters!

"

---

### Post by Eiríkr on 2008-03-25
For Lin-Lin sharing, Samba isn't necessarily your best bet -- Samba is all about Lin-Win sharing, and therefore includes all kinds of Windows-specific functionality that can just get in the way.  If you only need to share files via the browser between two Ubuntu systems, it's actually much simpler to install the [font=courier]ssh[/font] package on both, and then access by opening your Nautilus browser, clicking the location bar (usually hidden by default, but displayable by hitting Ctrl+L or clicking View -> Location Bar), and typing [font=courier]sftp://IP.ADD.RE.SS[/font], replacing the caps with the IP address of the other machine.  You'll then see a login prompt, into which you simply enter the username and password you use to log into that other machine, and then you get browser access to the filesystem.  No muss, no fuss, and no configuration needed.  

Cheers,

Eiríkr

---

### Post by gw4k on 2008-03-25
Hey there Eiríkr,

 You are the man!  Thank you very much for the information.  It works and it works great. 

You are a great example at why Ubuntu and Linux is wonderful to use.  I am not sure how to thank you on the forums here.  But you deserve it.

A side note for anyone looking to do the same thing.  If you need to find out what your ip address is ifconfig -a in the terminal.  Look at the inet addr: ***.***.*.***

Thanks again.

Also, if you want to install the ssh, do a search in your Synaptic Package Manager.  It will be towards the bottom in the list.  SSH.

Mark for install,
Then apply it.

Make sure to do this for all the computers you are wanting to connect with.

When you are ready to connect to that computer, Click places, computer (or other) and then hit CTRL + L to bring up the location bar.  Enter sftp://and the ip address number.

You will then be asked for the password and if you want the computer to remember it.

Thanks again everyone for the help.

---

### Post by adityakavoor on 2008-03-25
Welcome to the community and forums.

Mark the thread as solved

---

### Post by Eiríkr on 2008-03-25
Glad that worked for you, gw4k!  :D  And yes, please do mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  This way folks looking for an answer will know that this thread might have a solution for them.  :)

Cheers,

Eiríkr

---

### Post by gw4k on 2008-03-31
Thanks again everyone!  I have tons of questions just waiting to be answered!  haha

Again, you all rock!  Thanks for the help and welcoming me to the board.  Ubuntu, you are awesome as well!

---

