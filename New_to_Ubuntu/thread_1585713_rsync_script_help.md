---
title: "rsync script help"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by djyoung4 on 2010-09-30
Ok I have two different boxes and I want to keep the music synced up on both boxes.  My music on my laptop is stored in 
```
~/djyoung4/Music
```
and my music on my desktop is located in
```
~/home/Music
```
I'd like to use rsync and ssh and I have read a bunch of tutorials on them but haven't really figured it out.  Does anybody have any good scripts that will sync my music at a certain time of the day when both boxes are on.  Any help is greatly appreciated

---

### Post by mikechant on 2010-10-01
What sort of sync are you trying to do? Is one of these Music directories the 'master' and the other just supposed to be a copy of it, or is it possible you would update either on the laptop or the desktop and want the synchronization to go both ways?

---

### Post by Hippytaff on 2010-10-01
If it's just a one way thing, wouldn't a simple backup script work?

---

### Post by djyoung4 on 2010-10-01
> **mikechant said:**
> What sort of sync are you trying to do? Is one of these Music directories the 'master' and the other just supposed to be a copy of it, or is it possible you would update either on the laptop or the desktop and want the synchronization to go both ways?
it will go both ways.  Most of the stuff is the same but there are a few things on my laptop that I dont have on my desktop but a lot more stuff on my desktop that isn't on my laptop.  any ideas.  thanks for the responses

---

### Post by The Cog on 2010-10-01
Something like this should work as your script. 
> #!/bin/sh
LOCALDIR=$HOME/Sync/
REMOTEDIR=$HOME/Sync/
SERVER=192.168.1.103
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR $SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL $SERVER:$REMOTEDIR $LOCALDIR
You will need to adjust your LOCALDIR, REMOTEDIR and SERVER lines. 
You will need to make it executable. Assuming you call it syncMusic, use this command: **chmod +x syncMusic**

It is expecting to use passwordless ssh, so you will have to set that up: [http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private/Public+Key+Pair+on+Ubuntu/b5t6e](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private/Public+Key+Pair+on+Ubuntu/b5t6e)

Now you need to add this to your crontab file to have it run at the chosen time. Use  the command **crontab -e** to open an editor to edit the crontab file. If you're not sure about an editor, choose nano - it's the easiest to start with. A line like this should do it at 2:30:
> 30 2 * * * /home/whoever/syncMusic

---

### Post by djyoung4 on 2010-10-01
> **The Cog said:**
> Something like this should work as your script. 
You will need to adjust your LOCALDIR, REMOTEDIR and SERVER lines. 
You will need to make it executable. Assuming you call it syncMusic, use this command: **chmod +x syncMusic**

It is expecting to use passwordless ssh, so you will have to set that up: [http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private/Public+Key+Pair+on+Ubuntu/b5t6e](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private/Public+Key+Pair+on+Ubuntu/b5t6e)

Now you need to add this to your crontab file to have it run at the chosen time. Use  the command **crontab -e** to open an editor to edit the crontab file. If you're not sure about an editor, choose nano - it's the easiest to start with. A line like this should do it at 2:30:
Your link says the page is not found.  Thanks for the script though and is there any security problems that can come from making it a passwordless ssh connection

---

### Post by Neezer on 2010-10-01
> **djyoung4 said:**
> Your link says the page is not found.  Thanks for the script though and is there any security problems that can come from making it a passwordless ssh connection

I think he may be assuming that you have key encryption enabled....if you don't, I would highly recommend that you use authentication keys for ssh connections that are open to the internet.

Is this backup taking place just over the LAN, or is it from one LAN to another over the internet?

---

### Post by djyoung4 on 2010-10-01
> **Neezer said:**
> I think he may be assuming that you have key encryption enabled....if you don't, I would highly recommend that you use authentication keys for ssh connections that are open to the internet.

Is this backup taking place just over the LAN, or is it from one LAN to another over the internet?
It will be over the LAN.  I have WPA2 and MAC address filtering for security.  Is key encryption enabled by default over an LAN

---

### Post by tgm4883 on 2010-10-01
> **djyoung4 said:**
> Your link says the page is not found.  Thanks for the script though and is there any security problems that can come from making it a passwordless ssh connection

He means this

[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

The issue arises if one of your two machines is compromised. Then the attacker could login and run commands on your other machine.

---

### Post by djyoung4 on 2010-10-01
> **tgm4883 said:**
> He means this

[http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)

The issue arises if one of your two machines is compromised. Then the attacker could login and run commands on your other machine.
ok that makes sense.  So opening up this passwordless connection means its making a tunnel in between the two machines that nobody can access without the public keys.  is that right.

---

### Post by tgm4883 on 2010-10-01
> **djyoung4 said:**
> ok that makes sense.  So opening up this passwordless connection means its making a tunnel in between the two machines that nobody can access without the public keys.  is that right.

Not exactly.

What it means that instead of using a username/password to authenticate who you are instead it uses a public/private key pair. If an unauthorized user got a hold of your private key (or gained access to your machine), this would automatically give them access to the other machine as well.

Depending on how security conscious you are, you may want to look at the authorized_keys man page (specifically the command= portion). You can find that here [http://man.he.net/man5/authorized_keys](http://man.he.net/man5/authorized_keys)

---

### Post by djyoung4 on 2010-10-01
> **tgm4883 said:**
> Not exactly.

What it means that instead of using a username/password to authenticate who you are instead it uses a public/private key pair. If an unauthorized user got a hold of your private key (or gained access to your machine), this would automatically give them access to the other machine as well.

Depending on how security conscious you are, you may want to look at the authorized_keys man page (specifically the command= portion). You can find that here [http://man.he.net/man5/authorized_keys](http://man.he.net/man5/authorized_keys)
and the chances of this actually happening are what.  sorry for getting off track a bit.  I just want to understand whats going to be happening with this script and the downsides it could have

---

### Post by tgm4883 on 2010-10-01
> **djyoung4 said:**
> and the chances of this actually happening are what.  sorry for getting off track a bit.  I just want to understand whats going to be happening with this script and the downsides it could have

It really depends on you. Your private key is going to be stored in you .ssh folder. If you have it stored elsewhere (like on a usb stick), obviously the chances go up that it can get stolen. Comparing the two methods, I would use private/public key pair over password login.

---

### Post by djyoung4 on 2010-10-01
> **tgm4883 said:**
> It really depends on you. Your private key is going to be stored in you .ssh folder. If you have it stored elsewhere (like on a usb stick), obviously the chances go up that it can get stolen. Comparing the two methods, I would use private/public key pair over password login.
ok thanks for all the help.  Ill try and get this going and If I have any problems Ill post back.

---

### Post by The Cog on 2010-10-02
Sorry the link didn't work. I don't understand that. I'll try again:
EDIT: Still didn't work. Most odd.
I just googled for "passwordless ssh ubuntu" and looked at the top few results. That one seemed a fairly good explanation.

Setting up password-less ssh involved putting an identification key from the client PC into the list of trusted clients on the server. IF someone else got a copy of that key, they could also gain a login to the server without using a password. If you want scripted logins, it's something you'll have to live with. You could always put the keys in folder that's encrypted when you're not logged in (maybe encrypt your entire home folder). But that's still not perfect because an exploit while you're logged in might be able to get the keys. It you're really paranoid, you'll have to forego automated logins and sync manually, giving a password every time.

---

### Post by tgm4883 on 2010-10-03
> **The Cog said:**
> Sorry the link didn't work. I don't understand that. I'll try again:
EDIT: Still didn't work. Most odd.
I just googled for "passwordless ssh ubuntu" and looked at the top few results. That one seemed a fairly good explanation.

Setting up password-less ssh involved putting an identification key from the client PC into the list of trusted clients on the server. IF someone else got a copy of that key, they could also gain a login to the server without using a password. If you want scripted logins, it's something you'll have to live with. You could always put the keys in folder that's encrypted when you're not logged in (maybe encrypt your entire home folder). But that's still not perfect because an exploit while you're logged in might be able to get the keys. It you're really paranoid, you'll have to forego automated logins and sync manually, giving a password every time.

I disagree. IMHO, authenticated keys are more secure than user/pass authentication. To secure authenticated keys further, you need to read the man page on them. Specifically the command= section, which would allow only a certain command to be run on the machine no matter what was passed to it. There are many other ways to lock down authenticated keys as well, but thinking that user/pass is going to make you more secure than authenticated keys is IMO absurd.

---

### Post by The Cog on 2010-10-03
Try this link instead. It's probably a better description anyway. Deserves a higher google rank:[http://bodhizazen.net/Tutorials/ssh_keys/](http://bodhizazen.net/Tutorials/ssh_keys/)

@tgm4883:
It seems I didn't make myself clear. In no way did I mean to suggest that passwords were more secure than keys. I agree that keys are much more secure than passwords. I was just trying to point out that keys aren't necessarily perfect either. Keys can be stolen if the PC that holds them is broken into. But not only can passwords be keylogged under those circumstances, they can be guessed without any need to break into another PC first. So keys are safer.

Safest of all is a password protected key file, but of course you can't use automated logins with a password protected key file. Or can you? What man page are you saying I should read?
Edit: Ah, I got the Command= thing now. I followed the links at the bottom of Bodhizazen's page (linked above) on forced commands. That's a trick I wasn't aware of.

---

### Post by tgm4883 on 2010-10-03
> **The Cog said:**
> Try this link instead. It's probably a better description anyway. Deserves a higher google rank:[http://bodhizazen.net/Tutorials/ssh_keys/](http://bodhizazen.net/Tutorials/ssh_keys/)

@tgm4883:
It seems I didn't make myself clear. In no way did I mean to suggest that passwords were more secure than keys. I agree that keys are much more secure than passwords. I was just trying to point out that keys aren't necessarily perfect either. Keys can be stolen if the PC that holds them is broken into. But not only can passwords be keylogged under those circumstances, they can be guessed without any need to break into another PC first. So keys are safer.

Safest of all is a password protected key file, but of course you can't use automated logins with a password protected key file. Or can you? What man page are you saying I should read?
Edit: Ah, I got the Command= thing now. I followed the links at the bottom of Bodhizazen's page (linked above) on forced commands. That's a trick I wasn't aware of.

Yea I just learned about the command= thing myself after discussing it with a member of the ubuntu security team for a mythbuntu application I'm writing. Thats exactly what we will be doing for it, so even if the key is compromised, the attacker will only be able to run the specified command. We will be generating our own key as well, so that is the only thing that key will be able to do.

---

### Post by djyoung4 on 2010-10-03
should i run the script from my desktop or laptop

---

### Post by tgm4883 on 2010-10-03
> **djyoung4 said:**
> should i run the script from my desktop or laptop

Not sure I understand. If you are using ssh to run a script, it would need to exist on the machine you were running it on.

---

### Post by djyoung4 on 2010-10-03
> **tgm4883 said:**
> Not sure I understand. If you are using ssh to run a script, it would need to exist on the machine you were running it on.
well i have a desktop that is acting as the server but not headless and a laptop and I want to sync the music between the two.  should I have the script run on the laptop, the desktop or both in order to sync them

---

### Post by tgm4883 on 2010-10-04
> **djyoung4 said:**
> well i have a desktop that is acting as the server but not headless and a laptop and I want to sync the music between the two.  should I have the script run on the laptop, the desktop or both in order to sync them

I'd probably have the laptop run the rsync job. That way the server wouldn't be getting failures when the laptop is off. You could go either way though

---

### Post by djyoung4 on 2010-10-04
```
#!/bin/sh
LOCALDIR=~/djyoung4/Music
REMOTEDIR=~/home/Music
SERVER=178.178.7.127
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR $SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL $SERVER:$REMOTEDIR $LOCALDIR 
```
So theres the script im using.  Im running it from the laptop whos hostname is djyoung4 and the remote directory is home.  everytime i run it, it trys to ssh into djyoung4@178.178.7.127 but it needs to be home@178.178.7.127 and when i switch the directorys it says the same thing.  any suggestions.

---

### Post by The Cog on 2010-10-04
The command= configuration is configured on the SSH server, and references a script on the SSH server. When the user logs in, he sees the output from that command executing on the server rather than being given a command prompt where he can enter commands. Now I think about it, that option is probably not compatible with using rsync to synchronise folders because rsync will want to do its own thing.

The script I posted earlier would be run from the client - it makes the client connect to the server and sync folders with the folders on the server. In my house I have a server that sits in the corner. I use the script I posted on my other computers (desktop, laptop and netbook) to synchronise with the server. I don't do it in a cron job, I just do it by hand when I remember that one of the files has changed.

---

### Post by tgm4883 on 2010-10-04
> **djyoung4 said:**
> ```
#!/bin/sh
LOCALDIR=~/djyoung4/Music
REMOTEDIR=~/home/Music
SERVER=178.178.7.127
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR $SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL $SERVER:$REMOTEDIR $LOCALDIR 
```
So theres the script im using.  Im running it from the laptop whos hostname is djyoung4 and the remote directory is home.  everytime i run it, it trys to ssh into djyoung4@178.178.7.127 but it needs to be home@178.178.7.127 and when i switch the directorys it says the same thing.  any suggestions.

Looks like you need to login to the other server as a differnet user? Not sure how well that would work with authenticated keys, but you probably want to try and use a line like this. 

```
rsync --rsh=ssh -aizuKL $LOCALDIR $USER@$SERVER:$REMOTEDIR
```
Obviously you need to either have a $USER variable or stick "home" in there instead.

Also, just to confirm. Your remote directory is kept "/home/$USER/home/Music" and your local directory is "/home/$USER/djyoung4/Music"?

---

### Post by djyoung4 on 2010-10-04
> **tgm4883 said:**
> Looks like you need to login to the other server as a differnet user? Not sure how well that would work with authenticated keys, but you probably want to try and use a line like this. 

```
rsync --rsh=ssh -aizuKL $LOCALDIR $USER@$SERVER:$REMOTEDIR
```
Obviously you need to either have a $USER variable or stick "home" in there instead.

Also, just to confirm. Your remote directory is kept "/home/$USER/home/Music" and your local directory is "/home/$USER/djyoung4/Music"?
nope my music on the laptop is kept in "/home/home/Music" and the other is in "/home/djyoung4/Music

---

### Post by tgm4883 on 2010-10-04
> **djyoung4 said:**
> nope my music on the laptop is kept in "/home/home/Music" and the other is in "/home/djyoung4/Music

I ask, because the ones I have listed are what you specified in your script with 

```
LOCALDIR=~/djyoung4/Music
REMOTEDIR=~/home/Music
```

You probably want this instead

```
LOCALDIR=~/Music
REMOTEDIR=~/Music
```

---

### Post by djyoung4 on 2010-10-04
ok so heres what I get when I run the script
```
Syncing with 178.178.7.127
Sending...
home@178.178.7.127's password: 
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: mkdir "/home/djyoung4/Music" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.6]
Fetching...
home@178.178.7.127's password: 

```
I have no problem sshing into the server and once I enter the password again after it says fetching... the terminal closes
heres the script I have as of now:
```
#!/bin/sh
LOCALDIR=~/Music
REMOTEDIR=~/Music
SERVER=178.178.7.127
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR home@$SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL home@$SERVER:$REMOTEDIR $LOCALDIR 
```

---

### Post by tgm4883 on 2010-10-04
> **djyoung4 said:**
> ok so heres what I get when I run the script
```
Syncing with 178.178.7.127
Sending...
home@178.178.7.127's password: 
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: mkdir "/home/djyoung4/Music" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.6]
Fetching...
home@178.178.7.127's password: 

```
I have no problem sshing into the server and once I enter the password again after it says fetching... the terminal closes
heres the script I have as of now:
```
#!/bin/sh
LOCALDIR=~/Music
REMOTEDIR=~/Music
SERVER=178.178.7.127
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR home@$SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL home@$SERVER:$REMOTEDIR $LOCALDIR 
```

I bet it's pulling ~/ from the local machine rather than sending that remotely. Try hardcoding the full path in there instead of ~/

---

### Post by The Cog on 2010-10-04
The script assumes that password-less login is working (using keys).

If you want to log into the server using a different username than your own, then you will need to add the username to the rsync command as  tgm4883 suggests.

---

### Post by djyoung4 on 2010-10-04
so that would be
```
/home/djyoung4/Music
```
and
```
/home/home/Music
```
respectively correct?
note to self: don't name a box "home".  Problems arise

---

### Post by tgm4883 on 2010-10-04
> **djyoung4 said:**
> so that would be
```
/home/djyoung4/Music
```
and
```
/home/home/Music
```
respectively correct?
note to self: don't name a box "home".  Problems arise

That is correct

---

### Post by djyoung4 on 2010-10-04
works perfectly.  thanks tgm

---

