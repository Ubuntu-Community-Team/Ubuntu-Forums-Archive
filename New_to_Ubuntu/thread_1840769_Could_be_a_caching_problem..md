---
title: "Could be a caching problem."
date: 2011-09-08
forum: New to Ubuntu
---

### Post by MountainMan39 on 2011-09-08
I am new to Ubuntu and finding it all just as I expected - wonderful.

However, I have a problem.

I am updating files on a web server and doing some experiments with CSS.  Nothing too extra-ordinary.  when I edit a file on the server and then examine the effect in a browser (IE, Firefox or Chrome) the change is not visible in the CSS unless I rename the file and then update the links.

I am sure that this is something silly but I cannot find a solution.  

I apologise for saying this but it does not happen in W7

Thank you for any help

Tony D

---

### Post by haqking on 2011-09-08
> **MountainMan39 said:**
> I am new to Ubuntu and finding it all just as I expected - wonderful.

However, I have a problem.

I am updating files on a web server and doing some experiments with CSS.  Nothing too extra-ordinary.  when I edit a file on the server and then examine the effect in a browser (IE, Firefox or Chrome) the change is not visible in the CSS unless I rename the file and then update the links.

I am sure that this is something silly but I cannot find a solution.  

I apologise for saying this but it does not happen in W7

Thank you for any help

Tony D

Are you pressinf ctrl+f5 in your browser to refresh the cache ?

also you shouldnt really edit remotely, edit locally then upload to remote, and also have a back of up your existing site before changes ;-)

---

### Post by snip3r8 on 2011-09-08
What method are you using to edit remotely?

---

### Post by MountainMan39 on 2011-09-08
Thank you.

I agree I should not be editing remotely.  I will post again as to why I am doing that.  It is to do with my ignorance of Ubuntu.

I have used Ctrl/f5 and inbuilt browser techniques to flush the cache but to no avail.  There is also an application cache flush mechanism which I use.  Joomla / JA Template/ JAT3 Clean Cache

The editing is done in cPanel using the file manager and Code Editor.

Thank you for your help.

---

### Post by haqking on 2011-09-08
> **MountainMan39 said:**
> Thank you.

I agree I should not be editing remotely.  I will post again as to why I am doing that.  It is to do with my ignorance of Ubuntu.

I have used Ctrl/f5 and inbuilt browser techniques to flush the cache but to no avail.  There is also an application cache flush mechanism which I use.  Joomla / JA Template/ JAT3 Clean Cache

The editing is done in cPanel using the file manager and Code Editor.

Thank you for your help.


Editing remote or locally is nothing to do with Ubuntu, it is just good practice thats all.

So what happens when you make the changes locally then do a global PUT to your website ?

Are you using FTP client ? or built in app method for updating ?

I havent done anything web design related for a while but i used to use dreamweaver in a virtual machine.  I always have a backup opf my site locally and a back up of that.  I make changes locally then i delete the remote rather than sync to reduce conflicts the upload the local.  Unless of course the site is huge in which case files and dependants that have changed only.

---

### Post by MountainMan39 on 2011-09-08
I agree local or remote does not affect Ubuntu.

If I use a local host for some of the CSS experiments I get different results from using my remote host.  So I am using my remote host to do the work and, for that, the cycle edit, upload, test is slower than the similar cycle on the host.

When I upload I use either the file upload from cPanel or the Filezilla FTP.  No difference either way.

Each experimental site is only 20 or so files big so it is quite easy to sync each time.

When working in Windows I used to use PSP as editor with local and remote file access and the ability to control what went where.  For Ubuntu I have problems identifying something similar.  The description made Aptana sound good but I failed to install it.  Not clear why - everything seems to go OK but it is not installed.  The forums suggest it may be hard work.  And I tried others but they did not seem to fit the bill either.  Eclipse is a bit on the big side in my view.

So I find myself in a bit of a hole.

Thanks for your help

TD

---

### Post by 3rdalbum on 2011-09-08
What if you use something that ISN'T a browser (or is a fresh browser you haven't tried before) to retrieve the CSS file that has the change?

```
wget http://www.mysite.com/stylesheet.css
less stylesheet.css
```

If it still shows the old contents of the file, then you'll be able to tell if the web server is caching the file. If it's showing the new contents, and your web browsers are showing the old contents, then it's the browsers that are keeping the file cached.

---

### Post by mcduck on 2011-09-08
You could also try some developer extension (like the Web Developer Toolbar) that allows you to disable cache in the browser. Great feature for testing all kinds of things.

---

