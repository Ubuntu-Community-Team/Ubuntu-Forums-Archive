---
title: "Encrypting a folder"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by asharpham on 2010-05-05
I was just reading another thread about passswording a folder as I am interested in hiding or encrypting a folder in Documents.

The suggestion was:
gksudo nautilus /secret_folder
sudo chown -R user:user /secret_folder

However, I don't understand what has to be put into user:user. Also, does this need to be done as root or will normal user be okay?

---

### Post by GSF1200S on 2010-05-05
> **asharpham said:**
> I was just reading another thread about passswording a folder as I am interested in hiding or encrypting a folder in Documents.

The suggestion was:
gksudo nautilus /secret_folder
sudo chown -R user:user /secret_folder

However, I don't understand what has to be put into user:user. Also, does this need to be done as root or will normal user be okay?

I pulled this from:
```
chown --help
```

```
Examples:
  chown root /u        Change the owner of /u to "root".
  chown root:staff /u  Likewise, but also change its group to "staff".
  chown -hR root /u    Change the owner of /u and subfiles to "root".
```
Basically, you are specifying who you want to own it (user), and what group it belongs to (your username has its own group too).

If you put sudo in front of the command, you will be root. Since you are specifying who the user and group is, it wont hurt anything :)

---

### Post by asharpham on 2010-05-05
Okay, my username is alan so would I replace user:user with alan:alan? I'm not sure what the group is.

---

### Post by _0R10N on 2010-05-05
It's my understanding that the easy/best way for passwording a folder is using encryption. To do that right click on the folder and choose the Encrypt option. The problem with this approach is that you need to register a fingerprint, etc. It's not easy for newbies.

Personally, I don't encrypt valuable data individually. I use TrueCrypt for managing encrypted volumes. Then I put all my valuable data there. This is the really best way that I can recommend.

Now, if you what you really need is to prevent read/write access to certain files, then you can handle it with permissions configuration.

A little trick is to create another user. If you're alan, then create superalan. Use the previous comments to change the folder's owner to superalan. 
```
chown superalan MyValuableFolder
```
Then change the folder permissions like this:
```
chmod 700 -R MyValuableFolder
```
Now your folder can be accessed/modified only by superalan.
You can also make it a hidden folder, change its name to .MyValuableFolder.

Kind regards!

---

### Post by asharpham on 2010-05-05
Thanks for the advice. I downloaded & installed TrueCrypt and the linux front end, easy crypt. But there appears no relationship between what I see on the screen and the documentation.

Easy Crypt places an icon at the top of the screen to show it's operating but I can't see how to interact with it. Right clicking gives me a menu but nothing seems to happen when I select "Open the crypt". I've entered a password via the "Setup crypt" option and also looked at preferences (which i decided to leave at the default options) but can't see how to apply the software.

Any suggestions?

---

