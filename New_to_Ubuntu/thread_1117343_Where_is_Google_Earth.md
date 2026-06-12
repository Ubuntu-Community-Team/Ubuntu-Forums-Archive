---
title: "Where is Google Earth?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by jwaclawsky on 2009-04-05
I have Ubuntu 8.04. I used the Synaptic Package Manager to install Google Earth. I searched using the Synaptic package manager search and found:
googleearth-package 0.5.2. I selected/marked for installation and clicked apply. Everything went ok  ...as far as I can tell. It said it installed. But how do I start it?   I can find it anywhere?  I went to terminal and typed in "googleearh" and receivde "command not found". 

When I searched the file system for google earth I did find these files: 

googleearth-package_0.5.2_all.deb  /var/cache/apt/archives
googleearth-package.md5sums        /var/lib/dpkg/info 
googleearth-package.lst            /var/lib/dpkg/info
make-googleearth-package           /usr/bin
make-googleearth-package.1.gz      /usr/share/man/man1
googleearth-package                /usr/usr/share/doc

Any help would be much appreciated. Thanks.

---

### Post by alphacrucis2 on 2009-04-05
> **jwaclawsky said:**
> I have Ubuntu 8.04. I used the Synaptic Package Manager to install Google Earth. I searched using the Synaptic package manager search and found:
googleearth-package 0.5.2. I selected/marked for installation and clicked apply. Everything went ok  ...as far as I can tell. It said it installed. But how do I start it?   I can find it anywhere?  I went to terminal and typed in "googleearh" and receivde "command not found". 

When I searched the file system for google earth I did find these files: 

googleearth-package_0.5.2_all.deb  /var/cache/apt/archives
googleearth-package.md5sums        /var/lib/dpkg/info 
googleearth-package.lst            /var/lib/dpkg/info
make-googleearth-package           /usr/bin
make-googleearth-package.1.gz      /usr/share/man/man1
googleearth-package                /usr/usr/share/doc

Any help would be much appreciated. Thanks.

Add the medibuntu repos:

[http://www.medibuntu.org/]("http://www.medibuntu.org/")

Edit: Actually it looks like medibuntu only have V5 for the Jaunty repos. They have V4 for intrepid by the look. Also note that if you have trouble with it you should try running it it with compiz/desktop effects turned off as there are issues between OpenGL Apps and Compiz that haven't been sorted out yet IIRC.

---

### Post by GuitarRocker2562 on 2009-04-05
download it from google's site, or try googleearth-package

---

### Post by jwaclawsky on 2009-04-05
I am a novice. Could you be a little more specific. What do you mean by "try googleearth-package"? Thank-you

---

### Post by RedSingularity on 2009-04-05
Download the package from the google earth site.

---

### Post by llamabr on 2009-04-05
sudo apt-get install googleearth-package

---

### Post by RedSingularity on 2009-04-05
If that "package" doesnt work try [THIS](http://dl.google.com/earth/client/ge4/release_4_3/googleearth-linux-plus-4.3.7284.3916.bin) for the .bin file.  Very easy to install.  :)

---

### Post by alphacrucis2 on 2009-04-05
> **jwaclawsky said:**
> I am a novice. Could you be a little more specific. What do you mean by "try googleearth-package"? Thank-you

The google-earth package all set up for ubuntu is in the medibuntu repositories. You need to read the medibuntu howto here:

[URL="https://help.ubuntu.com/community/Medibuntu"]https://help.ubuntu.com/community/Medibuntu
[/URL]

Which explains how to add their repos to your package manager. Just follow their instructions and you will find google-earth will be available to install. The version offered though varies according to which version of ubuntu you are running.

---

### Post by jwaclawsky on 2009-04-05
Again could people be a little more specific. I am a novice. I downloaded the "package from google earth" and when I click on it I get "can't display..."  and "there is no file type fpr this application" Can some please explain. Thanks

---

### Post by RedSingularity on 2009-04-05
Is the package you downloaded on the desktop?  

Right click the icon on the desktop and go to properties>permissions>and make the file executable.

Then type this in terminal,

cd ~/Desktop
and then.......
sudo sh ./googleearth-linux-plus-4.3.7284.3916.bin

---

### Post by jwaclawsky on 2009-04-05
Thank-you shadow121. That did it. BTW, Before I did what you suggested, I went to Medibuntu and added the repositories with the following commands 

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

everything executed without errors. Did I do anything wrong? Again I am a novice and not quite sure what I am doing  :-)   ....but reading and trying. 

Thanks again for your assistance.

---

### Post by jwaclawsky on 2009-04-05
...wait  :-(   it "was" working. After I did the install it started up and put an icon on my desktop labeled "google-googleearth.desktop". But when I click on the icon, I get "can't display..."  "the location is not a folder"  Anyone know how to start Google Earth after it is installed? Many thanks for any assistance.

---

### Post by RedSingularity on 2009-04-06
Did you try from the terminal??

Try this without quotes "sudo googleearth"

---

### Post by stchman on 2009-04-06
Ubuntu has a nice help page on installing Google Earth.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

It took me all of 30 secs to locate this.

---

### Post by Benlap on 2009-04-06
I'm also trying to install Google Earth, using the terminal. When I type the line "sudo sh ./GoogleEarthLinux.bin", the line "[sudo] password for benlap:" appear. I try to type my password, but nothing is typing in... What can I do to go around this problem?

---

### Post by 3rr0r on 2009-04-06
> **Benlap said:**
> I'm also trying to install Google Earth, using the terminal. When I type the line "sudo sh ./GoogleEarthLinux.bin", the line "[sudo] password for benlap:" appear. I try to type my password, but nothing is typing in... What can I do to go around this problem?

Its typing your password as you press the keys.  It just doesn't display it on the screen (good security you see).  Just  type your password and hit enter.

---

