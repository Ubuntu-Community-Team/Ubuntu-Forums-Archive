---
title: "possible ecryptfs problem 10.10"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by PPN13 on 2011-05-09
So I booted my computer today and upon logging to my user account i got the following error 

```
Could not update ICEauthority file /home/sotiris/.ICEauthority
```

after clicking on ok i got another error 

```
There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
```

and thirdly an error that Nautilus cound not create my Desktop folder and a .Nautilus folder in my home. 

After that there was nothing. Not like a lockup but more like there was nothing to display. I decided to switch to tty1 and try to delete .ICEauthority to see if it could fix the problem.

Upon logging in tty1 i saw that i had to run ecryptfs-mount-private to access my home folder since its encrypted. Upon executing it asked my for my login passphrase. 

After that i get 
```
Inserted auth tok with sig [snip] into the user session keyring
You do not own that encrypted directory
``` and then back to prompt with my home not mounted.

It should be noted that the sig does not match what i 've got on my usb stick from the time i installed ubuntu. The system is fine otherwise and i m logged in at a guest account i made to make this post. So i think its probably an ecryptfs issue which causes gnome to fail to read its config and contents. For what it's worth i can confirm that /home/sotiris has my user account as its owner via nautilus in the guest account.

I also now have a 11 04 live cd on hand ( i 've misplaced my 10.10 but i wanted to upgrade anyways just didn't get around to doing it. So its not a life or death issue but i would prefer to 'solve' it rather than 'run away'.

Please advice, thank you.

---

