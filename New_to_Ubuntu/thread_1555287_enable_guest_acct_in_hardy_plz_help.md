---
title: "enable guest acct in hardy? plz help"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by stevek123 on 2010-08-17
I run 2 home computers networked behind a router. One is Hardy - the other is Karmic. I have enabled the folders I want shared and they share just fine between each other. I do not want/need passwords for the comps behind my router for any of these shared folders. Samba is installed on both... 

My daughter needed to acquire a new comp = MacProBook, for college (REQUIRED to attend class!). Nice laptop for sure. It runs Snow Leopard OSX 10.6.4. She wants to transfer her music (>20GB) to her laptop. Getting the Karmic machine to enable samba sharing including the guest acct was as easy as hitting the buttons under share options. Her comp grabbed those files without issue. 

The Hardy machine (where MOST of the music is) does not share with hers. Those files are enabled for anyone to read/write under ->properties ->permissions. OK... so I went to -> Properties -> Share, and enabled Share and allow others to write. It does NOT give option for guest acct (stays grey). THEN when I hit 'Create Share' it does NOT. It gives me an error message....   =  'net usershare' returned error 255: net usershare add: failed to add share mp3. Error was Operation not permitted

I went and looked at the Ubuntu Community Wiki and several google hunts = they may as well be in a foreign language. What do I do???????????

---

### Post by marshmallow1304 on 2010-08-17
Did you just now install Samba on Hardy?  If so, you should try rebooting that machine to make sure your user is in all the correct groups.

---

### Post by stevek123 on 2010-08-17
Thanks - but I tried that already.   and now that I think of it , No I didnt 'just install it' I did that >2 yrs ago when I still ran winXP and needed it to share then...

---

### Post by t0p on 2010-08-17
Um, maybe I'm missing something here.  But can't she transfer music files from Hardy to her MacBookPro over ssh?

---

### Post by skatinjj on 2010-08-17
> **stevek123 said:**
>  when I hit 'Create Share' it does NOT. It gives me an error message....   =  'net usershare' returned error 255: net usershare add: failed to add share mp3. Error was Operation not permitted

Someone can correct me if I am wrong since I am just getting back into Linux after a year break.

Sounds like you just need the right level of permission.

I believe you can open a terminal and run this:

```
sudo chmod 777 "directory path or file path"
```

Replace "directory path or file path" with whatever path you want to share.

sudo gives you root privileges for the command.

chmod 777 will give everyone permission to the directory/file you provide.

---

### Post by stevek123 on 2010-08-17
Sorry - whats ssh?

---

### Post by stevek123 on 2010-08-17
When she accesses the Hardy machine and tries to open anything - it says permission denied, guest acct not enabled.

---

### Post by stevek123 on 2010-08-17
skatinjj - there are a list of folders I have that she would like to grab. Do I need to do that individyally for each one or can I do it in batch (How?)

---

### Post by skatinjj on 2010-08-17
> **stevek123 said:**
> skatinjj - there are a list of folders I have that she would like to grab. Do I need to do that individyally for each one or can I do it in batch (How?)

I'm pretty sure all you have to do is put a comma after each path and you can just do them all with the one command line.

---

### Post by stevek123 on 2010-08-17
I ran  ' chmod 777 /... '  for one of the folders and made my girl go transfer it. Its running fine! Thanks!!! It got the job done...I'll get the others modified later :)

but still didnt enable guest acct - no answers so the method must not be simple.

---

### Post by skatinjj on 2010-08-17
> **stevek123 said:**
> I ran  ' chmod 777 /... '  for one of the folders and made my girl go transfer it. Its running fine! Thanks!!! It got the job done...I'll get the others modified later :)

but still didnt enable guest acct - no answers so the method must not be simple.

Sorry I overlooked that part.....

check [this]("https://help.ubuntu.com/community/SettingUpSamba") out, and if you need more help just ask.

---

### Post by stevek123 on 2010-08-17
LOL THATS one of the pages I already found and by the time I was halfway thru reading it I wanted to punch someone. Maybe someday I will be at that 'level of geek' but not yet :)~

---

### Post by skatinjj on 2010-08-17
> **stevek123 said:**
> LOL THATS one of the pages I already found and by the time I was halfway thru reading it I wanted to punch someone. Maybe someday I will be at that 'level of geek' but not yet :)~

With a guest account setup open a terminal and run:

```
sudo  smbpasswd -a username
```

Replace username with the name of the user that wants access (setup on the pc/server), then type what you want their samba password to be when it asks.

Next, run this:

```
sudo smbpasswd -e username
```

That will enable the user.

Once again replace username with the name of the user.

---

### Post by stevek123 on 2010-08-18
FWIW - I ran 'sudo chmod 777 /home/....' on several folders. My daughter's MacBook was able to access the first folder I did /mp3 -  but none of the other folders that I added after.    .../Music   .../Pictures, etc.
I am not sure what I did that was different but it mounts that /mp3 readily and gives 'not found' msgs for the others.
I guess I'll have to set her up with the user acct after all...but that will have to wait til later cuz my Mum-in-Law is here in that computer room for the next week :{

---

### Post by skatinjj on 2010-08-18
> **stevek123 said:**
> FWIW - I ran 'sudo chmod 777 /home/....' on several folders. My daughter's MacBook was able to access the first folder I did /mp3 -  but none of the other folders that I added after.    .../Music   .../Pictures, etc.
I am not sure what I did that was different but it mounts that /mp3 readily and gives 'not found' msgs for the others.
I guess I'll have to set her up with the user acct after all...but that will have to wait til later cuz my Mum-in-Law is here in that computer room for the next week :{

Assuming you tried putting a comma after each path, maybe a bash file would work best (and it is the method I prefer when doing this kind of work).

You can open gedit and put this:

```
#!/bin/bash
sudo chmod 777 "directory/file path";
sudo chmod 777 "directory/file path";
```

and so on until you have all the directories listed.  Save the file where you can find it.  Then open a terminal and run:

```
sudo chmod +x /home/user/bashfile
```

Replace the example path with yours.  That will allow the file to be executed.

It will run the command separately for each specified path or you can set up a guest user and anyone who wants to copy stuff from any of your samba shares would just need the user name and password.

When I ran Ubuntu server a while ago, I just set it up a guest account with a password and copied files via ssh in a terminal.

---

