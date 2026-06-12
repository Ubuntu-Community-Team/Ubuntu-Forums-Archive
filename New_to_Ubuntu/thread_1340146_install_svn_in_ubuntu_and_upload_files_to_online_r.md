---
title: "install svn in ubuntu and upload files to online repository"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by kraghavan on 2009-11-28
Hello all,
im new to ubuntu,
i wanna know how to install svn in my ubuntu and upload files to a specific url say beans talk. 
i run ubuntu using vmware from my windows vista HOST os. ie ubuntu is guest here.
I hope some1 can help me in this regard as i like ubuntu and i work alot on codes which i need to update or upload in beanstalk website.
expecting some help,
thanks,

---

### Post by carl.davis on 2009-11-28
You can install Subversion by opening gnome-terminal and typing:

```
sudo apt-get install subversion
```

You should follow the instructions on the beanstalk website to get it working with their servers.

---

### Post by Some Penguin on 2009-11-28
There appear to be a number of different SVN clients available, some of which provide GUIs if that's your cup of tea.  See
[http://stackoverflow.com/questions/86550/is-ther]("http://stackoverflow.com/questions/86550/is-there-a-linux-ubuntu-svn-client-that-doesnt-suck")[e-a-linux-ubuntu-svn-client-that-doesnt-suck]("http://stackoverflow.com/questions/86550/is-there-a-linux-ubuntu-svn-client-that-doesnt-suck")
for a relevant Q&A.

Regarding uploads to specific places, normally the destination is specified when you check out a repository, not when you upload.  e.g.

svn co [http://foo.bar.baz/some_respository](http://foo.bar.baz/some_respository)

and when operating in the working directory tree associated with that repository, update/add/delete/commit/etc operations will use the corresponding locations in the repository.

If Beanstalk provides a standard HTTP interface to their hosted Subversion repositories, that's all you'll need to do.  If they don't, you might be stuck with whatever it is that they provide.

---

### Post by kraghavan on 2009-11-28
hello,
thanks for that. I kind of got whAT YOU said.when i checked the beastalk website it seems pretty simple to upgrade the code .
My concerns here include 
a. I instaled the svn folder in my ubuntu desktop and have created a user id and account to it, but i dont know how to go beyond that
b. this is a little tough to operate thro the terminal but i will get used to it. althou can u suggest a better or faster way to do it?
c. I wanna know how i can upload the changed source code file from my hard disc to the beanstalk repository if i had the url link to that file stored in the beanstalk website.
hope some1 helps to guide me in this ,
thanks,

---

### Post by carl.davis on 2009-11-28
Beanstalk suggests the following for getting started with SVN

[http://help.beanstalkapp.com/faqs/basics-11/getting-started-with-subversion](http://help.beanstalkapp.com/faqs/basics-11/getting-started-with-subversion)

---

