---
title: "Need a Way"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by MasterXandrex on 2007-07-26
All, 

Here's my situation and limitations:

My work workstation is a Windows XP PC to which I do have administratve rights. My server at home is a standard Ubuntu Linux (:guitar:) server. I need a way to share a directory (possibly a network directory) to my home from my work PC. 

Firstly, needless to say, I probably shouldn't be doing this do I need as low a profile as possible. Currently, I have a server setup and am able to SSH from work into the server. I cannot go the other direction in any way (nor do I really want to create an SSH server on my workstation). Does anyone know a way for me to do this? 

Thanks,

Xan

---

### Post by DJMatty on 2007-07-26
you could set up an FTP server and use that to transfer files between your server and your work pc...

Matt

---

### Post by MasterXandrex on 2007-07-26
You misunderstand, or I did not state. I need a way to pull files from my work PC without storing second copies in advance and without the use of server software on my workstation.

Basically I need a way for the client to share files with the server... a bit backwards I know.

Xan

---

### Post by DJMatty on 2007-07-26
Oh ok... well if you want to access stuff on your work pc, you will need to:

1) install some sort of server software to allow you access to that pc, could be remote desktop/vnc etc, or ftp server or whatever
2) if your company has any sense it will have a firewall between it and the internet, so you will need to get the firewall rules changed to allow you to access your work pc from the internet (and by your first post, you want to do this secretly, so I am guessing that you won't be able to get the firewall modified)

so I guess my answer to your question would be no.

However if you know what files you want to take from your work pc, why not transfer them to your home pc while you are there at work? (using an ftp server on your home pc, or many other methods)

---

### Post by MasterXandrex on 2007-07-26
While I appreciate you telling me that you have no idea how to accomplish my needs, I would have inferred that from a lack of response. Between you and me, I think the second option would have been better for you.

Xan

---

### Post by DJMatty on 2007-07-26
Nope...

But from what you have asked I tried to help originally... if what you are wanting to do is to connect to your work pc at any time from your home pc, your work pc is not gonna be a client, it's gonna be a server, it has to be listening on the public internet for your home pc to connect to it.

The only way you are gonna get the work pc to be the client and connect to your home pc is if you initiate the connection yourself, or run it on a timer or something.

I think the 'helpfulness' of my post would be to tell you that it can't be done in the way you are asking, whether you class that as helpful or not i'll leave up to you, I was trying to save you time in looking for a solution that doesn't exist.

There are ways that it could be done, however, they all involve your work PC waiting for something to trigger it to connect to your home pc, but they will all involve running some form of server software on your work pc.

sorry i can't help any further.

---

### Post by swampdweller on 2007-07-27
Yikes.
Recommending Matt for sainthood.
Recommending "How to Win Friends and Influence People" to Xan.
:)

---

### Post by DJMatty on 2007-07-27
That's Saint Matt to you ;)

---

### Post by MasterXandrex on 2007-07-27
Matt, three points:

Firstly, I apologize. I shouldn't have been quite so harsh in my reply. I do know that you were attempting to help and I do appreciate it. I was frustrated when I read the reply and lashed out. I did actually use a bit of your solution in my final solution.

Secondly, the solution which I have found, while not exactly what I was hoping for, will suffice for the short duration I wish to use it:

My original problem is that the files are being updated by others. While we rarely run into each other, I cannot simply copy, make changes over a period of hours or days and then come back and replace all the files. I installed an SFTP server on my server at home, I then established protected directories which I could sign into and write. I then simply used a program which would sync the files in the directories I needed with the share anytime a file was modified. I also used this program to Sync one small file every 15 minutes so as to keep the connection alive. While this solution does not work as directly as I hoped my solution would, it does accomplish my needs.

Finally,  it is impossible to state that a solution does not exist as, if I really wanted to, I could write my own solution. Always remember, anything that is within the nature of a computer to do can be done by clever programmer and determined user.


Xan

---

### Post by DJMatty on 2007-07-27
Hehe, no problem, glad you got a solution that worked for you!

Looking back I could have asked a few more questions about what you were trying to achieve to see if we could get to a solution that solved the problem for you. So sorry for that, and I'll take that on board the next time I try to answer a question.

Matt

---

