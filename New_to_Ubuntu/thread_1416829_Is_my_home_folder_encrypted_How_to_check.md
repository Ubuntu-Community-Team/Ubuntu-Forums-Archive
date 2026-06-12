---
title: "Is my home folder encrypted? How to check?"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by kramer65 on 2010-02-26
Hello,


I want my home folder to be encrypted so that when my pc is stolen people will not be able to simply read out everything on my home folder (using a live cd). So I clicked the option "require my password to log in and to decrypt my home folder" in the installation process. 

When I first logged in it said something about a passphrase or something. I was busy doing some other stuff and clicked it away. But now I don't know if my home folder is actually encrypted, and whether I still need to set a passphrase (in case my system crashes..).

Could somebody give me some tips on how to make sure its properly encrypted and how I would be able to recover things in case it goes wrong?

---

### Post by ubunterooster on 2010-02-26
Boot from live cd (i prefer knoppix, as it gives root access by default).
Try to read home folder of hdd.
Post back here.

---

### Post by CharlesA on 2010-02-26
You'd need the passphrase to recover the data.

---

### Post by kramer65 on 2010-02-26
@ Ubunturooster
I started my pc with the Ubuntu live cd and went into the terminal (which I am not so good at, so I might need some help). I typed "cd /media/bed300d6-etcetc" (the HDD). I then typed "cd kramer" but it says permission denied. I then tried "sudo cd kramer and it says command not found. 
Does this mean my home folder is encrypted?

@ CharlesA
But I never wrote the passphrase down. Am I still able to get it from somewhere? (I can still log into the system)

---

### Post by ubunterooster on 2010-02-26
I mentioned knoppix because ubuntu liveCD does not give any root privileges (required for mounting other OS partitions)

---

### Post by kramer65 on 2010-02-26
Is that the only way of checking whether my home folder is encrypted? (since it takes some time to download and burn 700 mb..)

Also, do you know of any way to get the passphrase if I didn't write it down the first time..?

---

### Post by Paddy Landau on 2010-02-26
> **kramer65 said:**
> how I would be able to recover things in case it goes wrong?
At the moment, it's really difficult (and impossible for a layperson) to recover an encrypted folder -- even when you do have your 32-character unlock code. I did manage when a friend's computer crashed, but only after a tremendous amount of searching and experimentation.

There are moves afoot to make it easier to handle encrypted folders, but probably that will be a while coming.

The best thing to do is to **make proper backups**. That way, when something goes wrong, you have access to all your data. If necessary, you can reinstall and restore your data.

---

### Post by kramer65 on 2010-02-26
@ Pappy
Thanks for the explanation. I indeed already make backups, but I would still like to have my home folder encrypted (in case my pc gets stolen) and while I'm at it, why don't I try to also get this 32-character passphrase?

So does anybody know whether it is still possible to get this passphrase from somewhere?

---

### Post by Paddy Landau on 2010-02-26
> **kramer65 said:**
> So does anybody know whether it is still possible to get this passphrase from somewhere?
Yes, it's possible, but I found it so hard to discover how, that I'm afraid I don't have the answer for you.

Is your folder encrypted? Have a look at the file /etc/fstab. If you see something called "ecryptfs" on the same line as "/home" then, I believe -- someone tell me if I'm wrong -- your folder is encrypted.

Sorry to be so vague, but I find encrypted folders really hard to unravel.

---

### Post by kramer65 on 2010-02-26
Thanks for the info. You don't happen to have a link or anything to find out how to find my passphrase?

I had a look in the file you mention, but I don't see anything with "crypt" in it.

When I start up my pc however, it shortly shows some line which displays my home partition name and something like "init ecrypt". At least I saw the word "crypt" in it. Doesn't that mean that it is encrypted?
Also I am pretty sure I chose the "require my password to log in and to decrypt my home folder", so that would make the home folder encrypted right?

Well, the main thing is that I am after the passphrase actually.. Any help on that possible? :D

---

### Post by ubunterooster on 2010-02-26
sounds encrypted. Of course w/ backups, if someone steals them when they are not encrypted....

Sorry, can't help w/ passphrase

---

### Post by Post Monkeh on 2010-02-26
> **ubunterooster said:**
> I mentioned knoppix because ubuntu liveCD does not give any root privileges (required for mounting other OS partitions)

er, yes it does. any live cd will give you full root access.

if you go into an ubuntu live cd and simply open your hard disk containing your home folder, it should show your folders. if it doesn't show them as you see them when you log in then it's encrypted.

i haven't played much with it but you need the password that you forgot to note down if you ever have to reinstall and want to keep your files

---

### Post by kramer65 on 2010-02-26
I found it:

just run ecryptfs-unwrap-passphrase and voila; it's there.. :-)

Thanks anyway!

---

### Post by Jive Turkey on 2010-02-26
I just tried this on my laptop with encrypted home folder and checked it with my recorded passphrase and they matched.
execute:```
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
```
it prompts you for "Pasphrase:" but it really just wants your normal login password.  after entering it it will print the passphrase that you would need for the long arduous process of recovering your data (I think).  Save that passphrase somewhere apart from your laptop.

---

### Post by kramer65 on 2010-02-26
Great thanks!

I already saved it in a file and I just put it on a memory stick which I will hide away somewhere else.

Thanks a lot!

---

### Post by Paddy Landau on 2010-02-27
Here are some links that I have. Watch out: The procedures in the first two links are incomplete, but they do give you some important background.


[LIST=1]
[*][eCryptfs official Ubuntu Community documentation]("https://help.ubuntu.com/9.10/serverguide/C/ecryptfs.html")
[*][Ubuntu's encrypted home directory]("http://www.linux-mag.com/id/7568/1/") (three pages)
[*][eCryptfs "read me" document]("http://ecryptfs.sourceforge.net/README")
[*][Recovering Files from eCryptfs Encrypted Home]("http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/")
[/LIST]
And here is something for you to vote on:

[LIST]
[*][Encrypted home directory GUI tool is needed]("http://brainstorm.ubuntu.com/idea/22851/")
[/LIST]
Good luck.

---

### Post by gridd on 2010-02-27
Does this mean that all They have to do is. Steal (break in Hack?) someones PC laptop. then post on these forums and viola They have  stolen all your private encrypted data.  The thought police will love this one.

---

### Post by Post Monkeh on 2010-02-27
> **gridd said:**
> Does this mean that all They have to do is. Steal (break in Hack?) someones PC laptop. then post on these forums and viola They have  stolen all your private encrypted data.  The thought police will love this one.

no, because to recover the encryption passphrase you need to log in to the user account that has the encrypted files, by which stage the information is decrypted anyway.

---

### Post by Paddy Landau on 2010-02-28
> **Post Monkeh said:**
> no, because to recover the encryption passphrase you need to log in to the user account that has the encrypted files, by which stage the information is decrypted anyway.
Which leads me to remind you that your data is only as safe as your password. If your password is a simple word, hackers with physical access to your hard drive can probably break into it in a few minutes.

[How to choose a good password]("http://www.google.com/search?hl=en-GB&q=how+to+choose+a+good+password&sourceid=navclient-ff&rlz=1B3GGGL_enGB285GB285&ie=UTF-8&aq=1&oq=how+to+choose+a+good+pass")

---

