---
title: "Networking Ubuntu with Vistaa"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by thedragon4453 on 2007-05-15
Ok, So this is a silly question, but here goes.

I have set up a network with my ubuntu PC and my windows pc. I can see both computers under either computers "Network" folder.

The only problem I am having, is when it prompts me for a username. What do I enter? For example, say the username I use with vista is "Bob." When I enter "Bob" on the ubuntu prompt, and the password, it gives me a bad password error. The same is true with Vista.

So, what am I doing wrong?

Thanks.

---

### Post by foxmulder881 on 2007-05-15
Have you tried entering just the Username and no Password?

---

### Post by thedragon4453 on 2007-05-15
Even without a password it still fails.

---

### Post by trak87 on 2007-05-15
I ran into something similar today trying to connect from Linux to XP with the smbget utility. The solution was to use the same text for the password as the name. So try, bob and bob as the login name and password. That worked for me even though the computer I was connecting to was not set up with a password.

---

### Post by foxmulder881 on 2007-05-15
> **trak87 said:**
> I ran into something similar today trying to connect from Linux to XP.

The OP stated that the Windows system is Vista, not XP.

---

### Post by thedragon4453 on 2007-05-15
Using the same password as username didnt work. Either from the ubuntu pc to the vista pc, or vice versa

---

### Post by trak87 on 2007-05-15
> **foxmulder881 said:**
> The OP stated that the Windows system is Vista, not XP.

Yeah, I realized that. Sometimes the same techniques work across different versions. In this case it didn't work. It was a suggestion.

---

### Post by foxmulder881 on 2007-05-16
Did you get it thedragon4453?

---

### Post by thedragon4453 on 2007-05-16
no, im afraid not.

---

### Post by scott_rodgers100 on 2007-05-16
I'm told getting windows to see linux without the username / password prompts that accept none of either is not easy.  This fix worked for me but I also understand it is very in-secure.  Since I'm behind a firewall and I'm just testing now I figured it would be ok:

Get a command box:



sudo /etc/init.d/samba stop
sudo gedit /etc/samba/smb.conf

find lines that look like these:

"security=share"  "encrypt passwords=no" 

Just before the line type: "; I'm changing this"
Then put a ; in front of the "security=****" line
Then type in the "security=share" line
Do the same thing for the "encrypt passwords" line

save the file

sudo /etc/init.d/samba start

you should now be able to map the linux share to your xp machine without any annoying and unpassable username / password prompts.  You are also now valnerable to lots of nasties if you are not behind a firewall

---

