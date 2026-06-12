---
title: "Symbolic Linking for Dropbox"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by palantir6er on 2011-01-12
Hi everyone! First Post.
I have Ubuntu 10.10 installed on two laptops with Dropbox installed on each. I symbolically linked my documents, music, etc. folders to my home/username/Dropbox folder on computer 1 and I can see those files on computer 2. Great.

Now I want to be able to update files in documents, music, etc. on computer 2 and have that change the files in computer 1 also. I tried to symbolically link on computer 2 but the Dropbox folder already has folders from computer 1 in it:

On computer 2:
ln -s /home/username/documents ~/Dropbox
ln: creating symbolic link `/home/username/Dropbox/documents': File exists

I want the documents folder in Dropbox to contain the union of the documents contents for the two computers so why won't it let me do this?

---

### Post by blind2314 on 2011-01-12
Because that link already exists..sym links only point to one target, not multiple targets. If it was multiples, it wouldn't know which one to choose when the link was accessed or traversed.

---

### Post by davidmohammed on 2011-01-12
> **palantir6er said:**
> Hi everyone! First Post.
I have Ubuntu 10.10 installed on two laptops with Dropbox installed on each. I symbolically linked my documents, music, etc. folders to my home/username/Dropbox folder on computer 1 and I can see those files on computer 2. Great.

Now I want to be able to update files in documents, music, etc. on computer 2 and have that change the files in computer 1 also. I tried to symbolically link on computer 2 but the Dropbox folder already has folders from computer 1 in it:

On computer 2:
ln -s /home/username/documents ~/Dropbox
ln: creating symbolic link `/home/username/Dropbox/documents': File exists

I want the documents folder in Dropbox to contain the union of the documents contents for the two computers so why won't it let me do this?

If you've got dropbox installed on both laptops linked to the same account, you simply drop the file on computer 1 into the dropbox folder and they will reappear on computer 2 after a short while - and visa-versa.  Don't know why you need to use symbolic links at all.

---

### Post by palantir6er on 2011-01-12
I know I could drag and drop each file but I want all my folders to be synced automatically across computers. Since there is only one dropbox folder, I read ( [http://lifehacker.com/5154698/sync-files-and-folders-outside-your-my-dropbox-folder](http://lifehacker.com/5154698/sync-files-and-folders-outside-your-my-dropbox-folder) ) that I could do this by symbolically linking all my folders to the dropbox folder so that I don't have to change my directory layout and all the folders would be synced.

Maybe there is another way to achieve this?

---

### Post by davidmohammed on 2011-01-12
sounds like you want to use something like [unison]("https://help.ubuntu.com/community/Unison") to achieve what you want.

---

### Post by halcyonbuddha on 2012-09-10
How is this "solved"?!?  I have the same problem.  I want to sync web pages, etc., that I'm working on across my computers.  The reason I (and, I assume, the person who originally asked about this) can't "just throw all the files into Dropbox and access them across multiple computers" as was suggested is because we (LAMP users, I'm guessing) can't test PHP, etc. from Dropbox. HTML and CSS work fine, but if you want to test anything sever-side, the files have to be in the /var/www folder (as far as I know). I think we know how to use Dropbox for files and folders in general, but what we want is a way to sync our /var/www folders across computers (making them ONE folder via Dropbox?) so we can work on our web stuff when-/wherever.  Perhaps the problem was not clearly defined enough before, but I'm pretty sure somebody out there has a real solution for this, and I certainly welcome the advice. It will make my work/life that much more convenient! Thank you for your help and thanks to those who already posted answers, but I don't think you really addressed the problem yet. 
Anyway, thanks to you all. Cheers.

---

### Post by Gordonbp531 on 2012-09-10
> **halcyonbuddha said:**
> How is this "solved"?!?  I have the same problem.  I want to sync web pages, etc., that I'm working on across my computers.  The reason I (and, I assume, the person who originally asked about this) can't "just throw all the files into Dropbox and access them across multiple computers" as was suggested is because we (LAMP users, I'm guessing) can't test PHP, etc. from Dropbox. HTML and CSS work fine, but if you want to test anything sever-side, the files have to be in the /var/www folder (as far as I know). I think we know how to use Dropbox for files and folders in general, but what we want is a way to sync our /var/www folders across computers (making them ONE folder via Dropbox?) so we can work on our web stuff when-/wherever.  Perhaps the problem was not clearly defined enough before, but I'm pretty sure somebody out there has a real solution for this, and I certainly welcome the advice. It will make my work/life that much more convenient! Thank you for your help and thanks to those who already posted answers, but I don't think you really addressed the problem yet. 
Anyway, thanks to you all. Cheers.

Ubuntu One will do what you want. As well as the Ubuntu One folder, you can specify directories outside of the Ubuntu One folder anywhere on your computer to synchronise.

---

### Post by halcyonbuddha on 2012-09-10
Yeah, gendibal, I have used Ubuntu One for that before, and there's nothing wrong with it.  I just prefer to have Dropbox in case I have to develop on a Windows machine at work or a Mac elsewhere.  Otherwise, I agree that One is a simple solution. Thank you.

---

### Post by Gordonbp531 on 2012-09-10
> **halcyonbuddha said:**
> Yeah, gendibal, I have used Ubuntu One for that before, and there's nothing wrong with it.  I just prefer to have Dropbox in case I have to develop on a Windows machine at work or a Mac elsewhere.  Otherwise, I agree that One is a simple solution. Thank you.

Ubuntu One has a Windows port....

[https://one.ubuntu.com/downloads/windows/](https://one.ubuntu.com/downloads/windows/)

---

### Post by mcduck on 2012-09-10
Just create the link the other way...

For example, instead of linking your existing ~/Documents into ~/Dropbox/Doucuments, you can delete the local ~/Documents and then do "*ln -s ~/Dropbox/Documents ~/Documents*".

Afterwards you might have to check the ~/.local/user-dirs.dirs file and make sure it still points to correct directories, and fix it if some of the references got removed when you deleted a directory. Of course this should only be required for the pre-configured "special" locations like ~/Documents, ~/Pictures etc.

---

### Post by halcyonbuddha on 2012-09-10
> **mcduck said:**
> Just create the link the other way...

For example, instead of linking your existing ~/Documents into ~/Dropbox/Doucuments, you can delete the local ~/Documents and then do "*ln -s ~/Dropbox/Documents ~/Documents*".

Afterwards you might have to check the ~/.local/user-dirs.dirs file and make sure it still points to correct directories, and fix it if some of the references got removed when you deleted a directory. Of course this should only be required for the pre-configured "special" locations like ~/Documents, ~/Pictures etc.

That's what I'm trying to do right now, but Apache is defecating in my face over it.

---

### Post by mcduck on 2012-09-10
> **halcyonbuddha said:**
> That's what I'm trying to do right now, but Apache is defecating in my face over it.

Yopu might have to explain that inh a bit more detaiul for anybopdy to be able to help... ;)

Anyway, keep in mind that Apache's web site directories can be configured to be located where ever you want. So instead of using the default /var/www, you could just configure it to use a directory inbside your Dropbox directory without even having to mess with symlinks at all... (I wouldn't recommend that fopr a production server, though, but for any testing and development work it's perfectly fine)

---

