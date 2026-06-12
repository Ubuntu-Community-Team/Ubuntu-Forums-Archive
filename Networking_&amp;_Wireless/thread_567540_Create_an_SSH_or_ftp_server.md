---
title: "Create an SSH or ftp server ?"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by Sweet Spot on 2007-10-04
OK, so I've been reading several threads about both ftp ad SSH servers, and I'm no better off for having done so. In fact, I'm now more discouraged than when I set out to figure this out. 

Basically, all I want is for a friend of mine whom is a Mac user to be able to connect to me via either ftp or ssh server over the internet so that we can upload and download family vids and pics to one another. 

At first, I thought I could just connect to his server via Nautilus, (which I guess is possible) but upon further thought, I surmised that it would be nice to have it go both ways. So, if someone can tell me please:

What is the EASIEST way that my Mac toting friend and I can securely share files in a specific directory of mine or his ? I was looking at a pureadmin, but decided to cancel when it asked for my password to install it. I did not like that idea at all. Call me paranoid but... the only thing that should be asking for my password IMO, is Feisty. 

Note:  I am in no way skilled when it comes to any of this, so whatever the method is, it would be nice if it was contained in a GUI, or just an approach that an idiot can understand. 

Thanks a lot. 

Doug

---

### Post by kevdog on 2007-10-04
Are you guys going to be sharing them on the same LAN, or over the internet???

IF over WAN,

The easiest is ftp

The most secure is ssh.


Depends what you want to do. Are you always going to be the server, and he the client, or are both of you going to be both server and client???  For the mixed situation, he too would have to install server hardware on his machine.

ProFTP - here is a tutuorial: [http://ubuntuforums.org/showthread.php?t=79588&highlight=proftp](http://ubuntuforums.org/showthread.php?t=79588&highlight=proftp)

If you want ssh, I can tell you what to do.  Its easy to.

---

### Post by Sweet Spot on 2007-10-05
Over the Internet. I'm guessing that since he has a Mac, that it's equipt to handle such protocols and perhaps even comes with some ftp or ssh software ? Not sure though.  Well, he wants to send me some video files, so I suppose that I would need access to his end. But if I was acting as the server then he could just connect to me and send it that way, no ?

I guess which ever way is the easiest will do, but I really don't want to have to jump through hoops to achieve this. I can just hear him now: " damn dude, if you had a mac, we could achieve this so easily" etc... I've set up ftp servers on Windows using stuff like cuteftp and the likes, and it was a sinch. I didn't have to go through anything like I'm seeing on some of these threads regarding setting up a simple file sharing method via ftp or ssh... 

Doug

Edit: Yeah, I saw that proftp thread already, and what a freeking nightmare it looks like to set up ! Like I said, in Windows, I had easy to use programs with a GUI that would take care of everything mostly. This stuff looks like it's a lot more trouble than it's worth.

---

### Post by kevdog on 2007-10-05
Sorry I dont have an easier method.  FTP seems like it would be best for you.  What would your friend do??  Mac runs BSD down below and linux/bsd share many of the same packages.

---

### Post by Sweet Spot on 2007-10-05
Not really sure of what he would do to be honest. You said SSH would be easy to set up. Do you think it would be easier to set up than the former ? Thanks for your help. 

doug

edit: Gonna get some sleep before my 11-7 over night shift. Thanks again for any help you can and have provided. I'll check back before I leave at about 10 pm.

---

### Post by zyberwoof on 2007-10-05
> **Sweet Spot said:**
> 
Edit: Yeah, I saw that proftp thread already, and what a freeking nightmare it looks like to set up ! Like I said, in Windows, I had easy to use programs with a GUI that would take care of everything mostly. This stuff looks like it's a lot more trouble than it's worth.

You should look at the proftp thread again.  It has two parts.  

Part A has only two short steps to get your FTP server up and running.   The two steps for it are:  1. copy and past one line of text into your command line/terminal.  2.  Play with the GUI to get the server up and running.  

Part B is the long, evil looking command line part.  You can just do Part A instead.  

Honestly, I have never used the GUI for proftpd, so I can't tell you if it is good or not.  But it is worth a shot!  Good luck with it.

---

### Post by Sweet Spot on 2007-10-06
Zyber: So you basically installed via the "evil" looking method then ? Were there any hitches along the way, or any other links you had to refer to because of updates etc.. ? 

Thanks. 

Doug

---

### Post by xurios on 2007-10-06
For this sort of thing, I typically use the fish protocol in konqueror (the kde file/web browser. fish uses ssh to transfer the files I think). It's super easy. If I have an account on some remote machine, [email]joe@schmoe.com[/email] say, then in the address/file-path field in konqueror I type: fish://joe@schmoe.com

It asks for my password, and then I've got my home folder on the remote machine in a konqueror window in front of my face. I can drag and drop, whatever. No setup required for the konqueror part of things. Just make your friend an account on your machine that he  can ssh into (he can use konqueror on his mac too, the best version of it is available from the fink project), or he can make an account for you.

Also, in case you didn't already know, whoever is running the machine to be logged into will need a static IP address. This is true regardless of what software you end up using to get at each other's files over the internet.

---

