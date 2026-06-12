---
title: "installing fonts"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by PhilRogers34 on 2011-03-27
ok i have downloaded a font i would like to use but i cant get it to install i have been trying with the terminal but it wont have it, can someone please explain in basic simple steps how to install it,  if you need to give me codes then its a tff file and its in my downloads  thanks

---

### Post by Enigmapond on 2011-03-27
Very easy. Create a /.fonts folder in your home folder. Place the font in there and then do :

```
sudo fc-cache -f -v
```

This will update the font systemwide.

---

### Post by TeoBigusGeekus on 2011-03-27
See if you have a folder called .fonts in your home partition. If you don't, create it
```
mkdir ~/.fonts
```
Move the ttf file from your Downloads folder to the .fonts folder
```
mv ~/Downloads/fontname.ttf ~/.fonts
```
Log out, then log in and you should be fine.

---

### Post by PhilRogers34 on 2011-03-27
cool, thank you+, do i need to be lgged on as administrator? i downloaded it in my normalprofile which doesnt have permission to alter stuff

---

### Post by Enigmapond on 2011-03-27
> **TeoBigusGeekus said:**
> See if you have a folder called .fonts in your home partition. If you don't, create it
```
mkdir ~/.fonts
```
Move the ttf file from your Downloads folder to the .fonts folder
```
mv ~/Downloads/fontname.ttf ~/.fonts
```
Log out, then log in and you should be fine.

Just logging out and in again won't do it. The font cache still needs to be updated.

---

### Post by TeoBigusGeekus on 2011-03-27
> **PhilRogers34 said:**
> cool, thank you+, do i need to be lgged on as administrator? i downloaded it in my normalprofile which doesnt have permission to alter stuff

You can do whatever you want in your home folder - no permissions needed.

> Just logging out and in again won't do it. The font cache still needs to be updated.

Good to know that, thanks.

---

### Post by Enigmapond on 2011-03-27
> **PhilRogers34 said:**
> cool, thank you+, do i need to be lgged on as administrator? i downloaded it in my normalprofile which doesnt have permission to alter stuff

The "sudo" part in the code will give you temporary access to update the font. If you have permissions set where this is not possible, then yes. You would need to be an admin.

---

### Post by PhilRogers34 on 2011-03-27
thanks guys, i shall give it a go

---

### Post by PhilRogers34 on 2011-03-27
its not letting me name the folder /.fonts                     says i cant have slashes in the folder title

---

### Post by Enigmapond on 2011-03-27
Omit the slash...this was just a way to show it was your home folder. The folder should just be .fonts.

---

### Post by PhilRogers34 on 2011-03-27
doh!!! thanks

---

### Post by Enigmapond on 2011-03-27
No problem. Glad to help. When you have sorted it all out, please mark this thread as solved, for others' benefit.

Cheers!

---

### Post by theapplefan77 on 2011-03-27
thats awesome, now i know how to install fonts

---

### Post by PhilRogers34 on 2011-03-27
> **Enigmapond said:**
> Very easy. Create a /.fonts folder in your home folder. Place the font in there and then do :

```
sudo fc-cache -f -v
```This will update the font systemwide.


ok i have done that, how do i find an select the font when i want to use it?

---

### Post by Enigmapond on 2011-03-27
> **PhilRogers34 said:**
> ok i have done that, how do i find an select the font when i want to use it?

What are you trying to use it for? You can open your Preferences/Appearances and click the fonts tab and see if it's there. It should be.

---

### Post by PhilRogers34 on 2011-03-27
[FONT=Arial Black]i think i have it sorted now, does this how up properly?

[FONT=Arial]i think i have it sorted now, can you read the symbols above?[/FONT]
[/FONT]

---

### Post by PhilRogers34 on 2011-03-27
excellent, looks like i got it

thanks for the help, much appreciated!

---

### Post by Enigmapond on 2011-03-27
> **PhilRogers34 said:**
> [FONT=Arial Black]i think i have it sorted now, does this how up properly?

[FONT=Arial]i think i have it sorted now, can you read the symbols above?[/FONT]
[/FONT]

LOL well yes, but it won't have any bearing on posting here. The font is only on YOUR system..:)

---

### Post by PhilRogers34 on 2011-03-27
ok, any way i can make it show on other peoples systems?  and also it has only installed on one profile, it wont let me install it on my main profile, how do i install it so it's there for all profiles?

---

### Post by PhilRogers34 on 2011-03-27
ok so  just logged onto my admin account and installed a font, it's fine in the admin profile but hasn't installed to any other profiles, how do i get it to install in every profile?    my main profile keep sayin i dont have sudo access

---

### Post by PhilRogers34 on 2011-03-27
anyone?

---

### Post by PhilRogers34 on 2011-03-27
can somebody give me an answer please  i just made my main profile and admin and did exactly the same but the font hasn't installed, where am i going wrong and how do i get it toinstall  in every profile?

---

### Post by howefield on 2011-03-27
Please keep your bumps to once per 24(ish) hours.

Have you gone through the help page here ?

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by PhilRogers34 on 2011-03-27
i was hoping someone could just give me an answer,  my main profile wont let me create a .fonts folder, it says that a folder with that name is already in use in this folder.  so far i only have the font installed in the admin profile, how do i get it to install in every profile?

---

### Post by PhilRogers34 on 2011-03-27
no offence but someone just give me a god damn answer please, i posted in my original thread over an hour ago cos it hasn't worked prop[erly  ive been through the help pages and looked at what i can find, i've tried updating the fonts cache and nothing is working.  how do i delete the .fonts folder so i can recreate it in my main profile?

---

### Post by howefield on 2011-03-27
Duplicate threads merged.

---

### Post by SeijiSensei on 2011-03-27
What exactly do you mean when you refer to the "admin" profile?  Are you talking about the root user's profile in /root?  There is no "admin" user by default; if you created one it doesn't have the privileges you think it has.  

On Ubuntu you need to use "sudo," or in GNOME, "gksudo," to perform admin tasks.  

I suspect most of the rest of us don't know exactly what you mean either.  If you've modified your Ubuntu installation in some unique way, probably no one here can help very much.

---

### Post by PhilRogers34 on 2011-03-27
thanks but this issue isn't solved and as i cant unmark the thread i had to make a new one,

why cant you just give me an answer?

---

### Post by Enigmapond on 2011-03-27
I don't know the answer to this problem...I'm not sure why all the profiles have been set and have never had to deal with that.

However:

Everyone here is here helping on their spare time. If you don't get an answer right away, wait and one will come if someone can help. BUT, requesting help in this manor is not acceptable here and asking this way will only end up with either NO help at all or possibly a ban from the forum. There is no reason to be hostile. If you want immediate support...contact Canonical and subscribe.

Best of luck............

---

### Post by PhilRogers34 on 2011-03-27
right, i had one profile set as admin and one as a normal user.  the normal user is my main profile and the admin is for installing apps etc.

i logged onto the admin profile to install the font but it is only showing in the admin profile.

 i then changed the normal profile to an administrator but it still wont let me intsall the font, 
ive tried everything that was suggested in the thread in both profiles but it only worked in the original admin profile and not my main one.

i haven't ever used root.   i haven't got a clue how to access root anyway and was told i would never need to as i'm not into programming and developing. i just use my pc for music, films and the internet, basic everyday stuff

---

### Post by Dennis N on 2011-03-27
Fonts available to applications in all user accounts will be in /usr/share/fonts folder. You do need root access to place font files in there. You choose the font through the application you are using - applications have a drop down box to select one.

---

### Post by SeijiSensei on 2011-03-27
> **PhilRogers34 said:**
> i haven't ever used root.   i haven't got a clue how to access root anyway and was told i would never need to as i'm not into programming and developing.

Who told you this?  I wouldn't rely on that person for advice in the future.

Unless you run as the "root" user via [sudo]("https://help.ubuntu.com/community/RootSudo"), you cannot make system-wide changes, only changes to your own account.

Next time, perhaps, you'll do a little searching for documentation before coming here and screaming at everyone.

---

### Post by Enigmapond on 2011-03-27
> **seijisensei said:**
> who told you this?  I wouldn't rely on that person for advice in the future.

Unless you run as the "root" user via [sudo]("https://help.ubuntu.com/community/rootsudo"), you cannot make system-wide changes, only changes to your own account.

Next time, perhaps, you'll do a little searching for documentation before coming here and screaming at everyone.

+1:p

---

### Post by Wolligog on 2011-04-04
you could try, right click on the .tff file>select font viewer> install.  works for me!

---

