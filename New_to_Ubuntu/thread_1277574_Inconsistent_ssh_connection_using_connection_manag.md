---
title: "Inconsistent ssh connection using connection manager"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by pgibson on 2009-09-28
Hooray!  I've used the "Connect to Server" doohickey to connect from my laptop upstairs to the desktop downstairs!  I've been using ssh -X in the terminal to go between machines, then typing nautilus because I'm a visual thinker and find the gui more intuitive.  

And because I like the gui (ever notice that there's even a gui in penGUIn?) I wanted to work out how to do all this from the desktop using ssh, and I did.

But I'm puzzled, and hoping for illumination.

The downstairs computer has three user files, one for each memeber of the family.  Additionally, I've set up a "common" user file and called it "Jeeves" as a place we can all access to share (a share file?) stuff.  To do this I set up the server address in the connection manager as the IP address followed by /home.  Upon first click, that's where I nautilus opens up, too: the remote home folder.  But later, if I click the icon for the link to the remote file, it takes me instead to the root directory.

I've no problem navigating my way from /root to /home, but I wanted to set this up on all our computers, and this just adds a layer of complication.

So, why does this happen?  Can it be fixed to consistently ssh into the remote /home directory?  


Thanks for helping me learn.

---

### Post by hotstovejer on 2009-09-28
I personally would use SSHFS instead of what you're trying to do. X over SSH is ok, but SSHFS will actually mount the folder on your computer as another folder. 

Like at home, I can access my home folder on my machine from any other computer in the home with a simple command ```
sshfs username@ipaddress:/folderyouwanttoaccess /whereyouwanttomountitto/
```

Let me break that command down for you.

sshfs - is the command to connect.
username@ipaddress - the user account on the computer you are trying to connect to. So, you@192.168.1.5 if that's your computer's ip.
:/folderyouwanttoaccess - This is the name of the folder on the REMOTE computer you want access to.
/whereyouwanttomountitto - This is the location you want the remote folder to show up at. Like, create a folder in your home dir, and that part would be /home/you/folderyoucreated.


[http://fullcirclemagazine.org/issue-18/](http://fullcirclemagazine.org/issue-18/) has a full writeup on it if you need help.

Hope this works for you.

Jeremy

---

### Post by Penguin Guy on 2009-09-28
Set the following:
```

Service type: SSH
Server: <server_ip>
Folder: /home
User Name: <username>

```
Then check 'Add bookmark' and press connect. That might work.

As things are you will likely end up with a hacker on your computer pretty soon. To secure your SSH connection you should add [COLOR="Green"]SSH: ALL[/COLOR] to /etc/hosts.deny and [COLOR="Green"]SSH: 192.168.1.*[/COLOR] to /etc/hosts.allow - this blocks all connections from outside your house. You can do this by [running]("http://www.psychocats.net/ubuntu/terminal"):
```

sudo cp /etc/hosts.deny /etc/hosts.deny~ &&\
sudo cp /etc/hosts.allow /etc/hosts.allow~ &&\
echo 'SSH: ALL' | sudo tee -a /etc/hosts.deny &&\
echo 'SSH: 192.168.1.*' | sudo tee -a /etc/hosts.allow

```

---

### Post by t0p on 2009-09-28
> **hotstovejer said:**
> I personally would use SSHFS instead of what you're trying to do.

[...]

[http://fullcirclemagazine.org/issue-18/](http://fullcirclemagazine.org/issue-18/) has a full writeup on it if you need help.


[Full Circle #28]("http://fullcirclemagazine.org/issue-28/") (last month's issue) also has a feature on "Networking Ubuntu PCs With SSHFS".  Pretty helpful article.

---

### Post by pgibson on 2009-09-28
**Hotstovejer** and** t0p**, thanks for the links to Fullcircle mags ... I've glanced over the articles and they tell me more about sshfs (that I can comprehend) than I was ever able to find with misters Google and Wikipedia.  Any recommended Gui app for sshfs?  It looks easy enough, but I'm just curious.:)

I need to revisit sshfs because it is indeed exactly what I was imagining being able to accomplish.

**Penguin Guy**, you addressed my question directly, thank you.  Yes, I did click the "Add Bookmark" box, and I'm relieved because I *think* that I did everything else as you indicated, though I'll need to re-examine it (I'm thinking I simply wrote 192.168.1.*/home in the server box, but I'll double check. 

Regarding the rest of your post Penguin Guy, though I am intrigued by the notion of setting up ssh to be secured against the evil web nasties from beyond my router, I admit to some of the details of your script escaping my comprehension ... and I like learning.  

**Additionally, to anyone who might care to weigh in**, can Penguin Guy script be made to work with sshfs?  How will I be able to get in, if I desire, at a later date?

My brain is growing.  It is good.

---

