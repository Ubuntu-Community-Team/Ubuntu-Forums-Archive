---
title: "Extremely Frustrated :["
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by turntabletux on 2006-09-02
Hello Guys,

I really wanna give Ubuntu a shot, due to me never using it before and I want to try out the Gnome system. However, I am havin a great deal of trouble installing Ndiswrapper. I am sorry if this has alredy been posted, but I have yet to find the answer that I need.

I can get how to use Ndiswrapper, I've used it many times in Suse. I can configure my card once I have Ndiswrapper installed. There in lies the problem.

I know that Dapper does not come with the files ndiswrapper-utils and ndisgtk. I have downloaded them, they were .deb files, and try numerous ways of searching. Keep in mind that I am new to Ubuntu. I tried double clicking on the.deb file and I get "Error: Dependency is not satisfiable: ndiswrapper-utils." I tried using the commandline and Synaptic Package Manager. 

I have no clue how to install those two files. Does anybody know where I can get those files that should work. I can live without my WIFI. I need it for school, and I want to try and figure this out. Any help would be greatfully appreciated! Thanks for reading my novel lol. :P
-Ant

---

### Post by insyzygy on 2006-09-03
If you used synaptic and couldn't find it its probably because you didn't enable the universe repositories (the universe is programs that are compiled for ubuntu but not officially supported by ubuntu). For legal or whatever reasons they aren't enabled by default but its only a couple clicks away. By the way, I assume you actually manually downloaded the packages from the web. This is not usually the way to install packages in ubuntu. Usually installing programs involves using either, synaptic or apt-get. (synaptic is really a graphical interface to apt-get).
Synaptic is located  in the system menu->administration->synaptic package manager. First open synaptic. In the  settings menu select repositories and check all the additional repositories.  Now search for ndiswrapper. Check what you want and hit apply. For your info this can all be done in the console if thats more your style (its usually faster) by doing 
```
sudo apt-get install ndiswrapper-utils 
``` 
To edit the repositories manually the file is in 
```
/etc/apt/sources.list 
```
to search for packages in the console 
```
sudo apt-cache search <what your searching for> 
```

Synaptic/apt-get will automatically download other packages needed to fulfill dependency issues and in fact apt-get is in my opinion leaps and bounds ahead of Red Hat or Suse's package managers.

---

### Post by turntabletux on 2006-09-05
Thank you ver mych insyzygy for the response!

However the ndigtk is not on my ubuntu cd. Is there anyway I can download the file? Ad of right now I would rather have the GUI. Thanks a lot guys.I hope my Ubuntu experience becomes more enjoyable.

Ant

---

### Post by insyzygy on 2006-09-05
If you have installed ubuntu and have a network connection synaptic or apt-get will download the relevant files. (Note above I said in synaptic to check all repositories, I should have said check all repositories except the CD disk ones you want to be using the newest versions once ubuntu has installed not the ones on the CD.) 

I realized that I assumed that even though wifi wasn't working for you, you had a wired network connection working. If that is not the case then synaptic/apt-get won't work since they need to be able to download the files.

If you don't have a working network connection of any sort on the ubuntu computer you can dowload the files to a cd on a different computer and install them manually. I can tell you how if thats the case, but if you have an ethernet connection working synaptic/apt-get should download ndiswrapper once you have checked the additionally repositories (but not the cd ones) as I indicated above. Make sure in synaptic that you hit the reload button once you change the repositories that way it updates the programs that are available from the newly added repositories.

You may wish to look around here 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by turntabletux on 2006-09-05
Thank you very much for responding so quickly. I do feel stupid, forgeting about my wired connection. Although my other computers are always being used, still it did slip my mind.

Once again, thank you very much for responding quickly. I had just woken up and I decided to check if anyone responded. It is 4 a.m., but I think I am going to try it out. Thanks insyzygy!

Ant

---

