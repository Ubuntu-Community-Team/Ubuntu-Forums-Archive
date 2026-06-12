---
title: "Question Synaptic Package Manager"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by jquillian on 2010-03-18
I am trying to upgrade Thunderbird. The latest version is easy enough to download from the mozilla site. It is compressed as a tar file. Can someone give me a click by click method of getting the downloaded file into the Synaptic Package Manager? Or some other way to get the file to run?

Thanks

James

---

### Post by rahulshah on 2010-03-18
why dont you try downloading the .deb file. It would be very easy to install. or just do the following:

#sudo aptitude update

followed by

# sudo aptitude install mozilla-thunderbird

have fun:)

---

### Post by chaanakya_chiraag on 2010-03-18
The tar.gz file you download from Mozilla's website is all you need.  Just extract it (right-click -> Extract here), double-click on the folder just created, and double-click the run.sh file or something similar.  It should open Mozilla Thunderbird!

---

### Post by MelDJ on 2010-03-18
in terminal 
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```

followed by 
```
sudo apt-get update 
```

and finally
```
sudo apt-get install thunderbird
```

---

### Post by jquillian on 2010-03-18
There isn't a run.sh file. The only one similar generates a text file.


> **chaanakya_chiraag said:**
> The tar.gz file you download from Mozilla's website is all you need.  Just extract it (right-click -> Extract here), double-click on the folder just created, and double-click the run.sh file or something similar.  It should open Mozilla Thunderbird!

---

### Post by jquillian on 2010-03-18
Thanks, I have no idea what you are talking about but so I just cut and pasted your instructions into the terminal and Thunderbird 3+ is up and running.

> **MelDJ said:**
> in terminal 
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```followed by 
```
sudo apt-get update 
```and finally
```
sudo apt-get install thunderbird
```

---

### Post by Paqman on 2010-03-18
Using a .tar file is generally a bad idea, as you won't get any security updates or bugfixes. That's really bad for an email client. MelDJ's suggestion is best. Just be prepared for the fact you might be installing a new bleeding-edge version of Thunderbird every day.

---

### Post by MelDJ on 2010-03-18
the first command 'add apt-repository' adds the mozilla daily repository to your sources list. this enables you to install software from its repository.

the second command 'apt-get update' refreshes your repositories

and finally 'apt-get install thunderbird' installs the package thunderbird.

sudo is used in front of all commands as these are administrative tasks. sudo lets you run them as root as a normal user doesn't have administrative rights

---

### Post by Calais225 on 2010-03-18
thanks MelDJ,

I was reading along with this thread and learning.  After less than a month of using Linux, I think I understood what your directions meant.

guess I will keep on reading these topics and learning.  :popcorn:

thanks for breaking down the commands like that.

cheers,

Bill

---

