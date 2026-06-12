---
title: "installing software without internet on pc"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by Utkarsh Ray on 2010-11-28
I am using Ubuntu 10.10 i386 on a vm. When I tried to install softwares using software center, it asked a password and after entering it I got an error telling that it had failed to download certain files (.gpg and .gz files). When I tried to use the ubuntu cd to install the programs, it told that the information is outdated. Can I install programs by downloading those files with my mobile and transferring them to my pc? Any other suggestion? Please help.

---

### Post by karthick87 on 2010-11-28
You can download packages for offline installation [COLOR=Red]**[here]("http://packages.ubuntu.com/")**[/COLOR]

---

### Post by Utkarsh Ray on 2010-11-28
Thank-you very much.

One more question please.
Can I use the gui-apt-key
[http://packages.ubuntu.com/maverick/admin/gui-apt-key](http://packages.ubuntu.com/maverick/admin/gui-apt-key)
to load the gpg files into software repository
.
Because the files are going to be large and I use internet only on my phone.
Actually I'm completely novice to unix type systems, so I will need a little bit more help.
Is it possible to have all the softwares installed at the time of installing the OS?

---

### Post by sikander3786 on 2010-11-28
Or this might be an even better choice.

[http://keryxproject.org](http://keryxproject.org)

It would resolve all the dependencies itself...

---

### Post by karthick87 on 2010-11-28
Yes @sikander3786 suggestion is also good.[COLOR=Red]**Keryx**[/COLOR] is an  offline repository manager. It's like synaptic but it works on a  pendrive you dont installation.It can only install software in a  Ubuntu system,but you can download the updates or new packages in any  Linux, Windows or OS/X.

[COLOR=Red]**[TUTORIAL]("http://keryxproject.org/tutorial/")**[/COLOR]

---

### Post by Utkarsh Ray on 2010-11-29
Thank you, I've downloaded Keryx
Does reply 4 imply that I can use Keryx on Windows to download packages and updates and then transfer the files to Ubuntu and use Keryx to install the softwares?
Do the files which are to be downloaded help in installing 'every' software available in software centre?

---

### Post by karthick87 on 2010-11-29
Yes ofcourse you can download files from windows.

---

### Post by Utkarsh Ray on 2010-11-29
I followed your advice and ran Keryx on Windows. It downloaded 17 files and then it said
'Loading packages. Be patient it'll take some time' when it didn't do anything after 30 minutes, I started the project in Ubuntu also (which is in virtualbox virtual machine)
But it also didn't do anything, I saw the System Monitor of Ubuntu which showed the program to be 'sleeping'

Can you tell me where the gpg files and gzip are downloaded when Ubuntu Software Center downloads them. If I know the directory name then I could try copying the files in it and the programs could be installed?
Is it possible in above way?

---

### Post by dhiman33 on 2010-11-29
When software center installs anything, package files are downloaded to /vsr/cache/apt/archives....go there and u will find lots of deb files. U can copy them and use later in offline mode to install in another machine.

---

### Post by dhiman33 on 2010-11-29
Also when u are disconnected from net, try installing anything from software center, it would give an error... click on details.... u will see a list of links of packages which ubuntu failed to download. copy the links and download them from some other machine. Now u can install them offline.

---

### Post by Utkarsh Ray on 2010-11-29
I tried your advice but the directory /var/cache/apt/archive is inaccessible to me. It tells that I'm not the owner so I couldn't change the permissions. How to get around this?
I've downloaded some files using Keryx

---

### Post by dhiman33 on 2010-11-29
Press alt+f2. Now type "gksudo nautilus". It will give u root permission. Now try to go to the folder/first change permission then go into it.

---

### Post by Utkarsh Ray on 2010-11-29
Thank you, it helped me access the directory! But, still when I start Ubuntu Software Center it tells me failed to connect to the internet.
I think it is due to the naming of the files the files are named as in.releases.ubuntu.com_dists_maverick_release.gpg
You can help me by telling what the actual names of files are in that directory
I had copied the files in ./var/cache/apt/archive

---

### Post by dhiman33 on 2010-11-30
:confused:Ok, I couldn't understand whatever u said in that last post...so,...here I will simply explain a method that should work to install software(in *.deb packages) in an ubuntu installation which has never seen net connection.Try to open the *.deb file, and ubuntu software center should automatically install it. If it tries to update the repositories by downloading things before it installs the deb package, it would fail I think, and in this case u can't install the deb file. A guy named ivarn told me today in ubuntuforums that in this case u can open synaptic, go to edit, and select "repair broken packages". After this u should be able to install the deb package.

Also before/after repairing packages, u can try to open terminal, go into the folder where the deb files are, and type "sudo dpkg -i filename.deb" to try to install a file.

P.S...Hmm.. so u are Indian; are u a bangali? (explanation for non-indian guys----"bangali" is a person who speaks in bengali language)

---

### Post by Utkarsh Ray on 2010-11-30
Thank you for the advice.
I need a little bit of help.
I think that I've cooked-up a way which could solve my problems.
I noticed that the directory ./dists/maverick in Ubuntu CD has only a few files as compared to Ubuntu ftp site. I think that using Windows I'll download all the files in the online directory of maverick and then I'll add them to the directory in the Ubuntu CD; next, I'll use MagicISO to make a customised CD having all the files which the Software Center wants to download and use the CD as the offline repository for all the 3200+ softwares in the Center.
By default the CD has only the necessary files to install the basic Programs. So when I tried to use it as offline repository it didn't help to install extra programs.

Will this work?

---

### Post by anand_30 on 2010-11-30
I have a very simple method,its as suggested as dhiman but in simple way:-
1.Go to synaptic package manager.
2.Search for you software.
3.select it and mark for installation
4.Now don't apply changes,go to File>Generate package download script
5.Save script somewhere.
Script will be like
:```
#!/bin/sh
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/l/lacheck/lacheck_1.26-11.1build1_amd64.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/tex-common/tex-common_2.06_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-common_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/texlive-binaries_2009-5ubuntu0.2_amd64.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-doc/texlive-doc-base_2009-2_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/l/luatex/luatex_0.50.0-1_amd64.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-base_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-base_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/l/latex-xcolor/latex-xcolor_2.11-1_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/p/pgf/pgf_2.00-1_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/l/latex-beamer/latex-beamer_3.07-2ubuntu1_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/l/lmodern/lmodern_2.004.1-3_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-generic-recommended_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-pstricks_2009-7ubuntu3_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/p/prosper/prosper_1.00.4+cvs.2007.05.01-4_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/p/ps2eps/ps2eps_1.64-6build1_amd64.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-fonts-recommended_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-extra-utils_2009-7ubuntu3_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-font-utils_2009-7ubuntu3_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-fonts-recommended-doc_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-base-doc_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended-doc_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-luatex_2009-7_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/texlive-extra/texlive-pstricks-doc_2009-7ubuntu3_all.deb
wget -c http://in.archive.ubuntu.com/ubuntu/pool/main/t/tipa/tipa_1.3-14_all.deb

```
This is package download script for latex for my ubuntu.

6.Now copy each any every address into windows browser.and download packages related to one software in one folder(this will save your time later in ubuntu.)in my case i will save it into latex folder.

7.Now go into ubuntu ,access that folder using terminal.
8.Execute following command inside that folder:
```
sudo dpkg -iR ./
```
-i for install
-R for recursive(satisfies its dependencies so you don't have to install each and every *.deb and check for its dependencies.

Hope this helps.

---

### Post by dhiman33 on 2010-12-01
> **Utkarsh Ray said:**
>  I think that using Windows I'll download all the files in the online directory of maverick and then I'll add them to the directory in the Ubuntu CD; next, I'll use MagicISO to make a customised CD having all the files which the Software Center wants to download and use the CD as the offline repository for all the 3200+ softwares in the Center.
  

:KSYah, theoritically it should work.... go to "http://packages.ubuntu.com/maverick/" and download things u would like to have in ur offline repository. But, all these packages won't fit inside a cd! I even think a dvd won't fit everything unless u decide not to download the games. Someone else might tell u the total size of all the packages....and then there are also third party repositories... Anyway suppose u downloaded everything and wrote it in a dvd, now to install things offline... go to software sources and u will find something like "add volume" there. After u add ur dvd, the softwares will be installed from it.

Now I don't know if a pen drive/hard disk can be added to software sources list. U can download everything including games etc., save the packages in pen drive/hard disk, and install from there.

Now, what I think u really should want to do, is to make a custom ubuntu distribution of yours which contains much more softwares/games than the default installation. Actually I asked this question a few days ago in ubuntuforums and here's the link of the thread..."http://ubuntuforums.org/showthread.php?t=1632556".

The application "remastersys" seems to do it all(not ALL actually, as u can't fit all those applications in a dvd) but I couldn't install it and faced some problems...just read my thread to see it.

---

### Post by Utkarsh Ray on 2010-12-01
Following the advices, I've learned that .deb is .exe for Ubuntu. Am I correct in thinking that that the programs shown in Ubuntu Software Center have their SRC on the disk itself and Ubuntu downloads the files for security reasons and then stores them in cache. So, if I DL the files it wants to DL and keep it in the cache, I'll be able to install the programs.

I went to the /pool/... Of the Ubuntu site and saw loads of packages which one can DL and install like Windows or one can take the steps like fellow forum-members have advised to minimise the data usage (which I want to do)
or the best: use Ubuntu on a PC with the traditional internet connection, not the one using mobile phone (like I do) because it is the easiest way to enjoy Ubuntu.
I'll now install Ubuntu dual booting with Windows (virtual PC doesn't take advantage of hardware), get a USB internet dongle or borrow one from my friend and enjoy the Ubuntu. And inbetween I'll improvise a solution, involving minimum data usage and some ease.

I thank everybody for their useful suggestions.

---

