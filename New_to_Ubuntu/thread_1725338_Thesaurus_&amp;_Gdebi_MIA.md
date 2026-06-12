---
title: "Thesaurus &amp; Gdebi MIA"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by Vallar on 2011-04-09
Hello, 

As I posted before, I am a newbie to Ubuntu. However, upon advice, I tried to install gdebi. I managed to get all the dependancies and the main program from the internet and installed it using the sudo dpkg -i /path/*.deb and I didn't get any errors. 

After doing that, I had this little "Open with gedbi" in my right click menu. However, whenever I do click on that option, nothing happens. I tried to look for any "gdebi" program in my Application menu --nothing!

On the other hand, there is a moby-dict file located here:
[http://packages.ubuntu.com/maverick/dict-moby-thesaurus](http://packages.ubuntu.com/maverick/dict-moby-thesaurus)

I downloaded that program along with the optional packages. Again, I used the sudo dpkg -i /path/*.deb and everything worked fine through the terminal and no error were produced. Yet, it happened again; nothing in the Application menu indicated that there is a program there. 

How can I resolve this? (I don't have a direct internet connection to my Ubuntu laptop so I can't use Synaptic or Ubuntu Software Manager). 

Thank you very much and best wishes!

---

### Post by 123456789123456789123456 on 2011-04-09
from what I was able to find out about the program, it is a system tool, to install deb packages, automatically resolving the dependiences.  if it were installed correctly should be located under system somewhere.  I have not downloaded it as of yet myself to find out.  my suggestion is, if you don't see it.  use synaptic, with or without internet, to find and permintally remove the packages, use command line sudo apt-get install and the program name.  this requires internet access, but it will automaically download and install the program.

---

