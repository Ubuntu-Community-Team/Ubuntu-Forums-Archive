---
title: "Free money! Need Help. ICS wm6 Ubuntu"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by scenkner on 2008-08-13
I will paypal $5 to the first person that can help me connect Ubuntu to the internet through ICS on a WM6 Smartphone.  This is an easy $5 for someone experienced.

I have tried to follow the instructions found on this forum and others to no avail.

The instructions I am using are:
"
First, you need to make sure you have the right Ubuntu packages installed:

sudo apt-get install subversion build-essential

Now do the following in a terminal:

svn co [http://synce.svn.sourceforge.net/svnroot/synce/trun](http://synce.svn.sourceforge.net/svnroot/synce/trun)
/usb-rndis-lite
cd usb-rndis-lite/
make
sudo ./clean.sh
sudo make install
"

sudo apt-get install subversion
-Cant find the package

I do not currently have any way to connect my PC to the internet other than the ICS through WM6.  That is how I am able to get on here.  I am using a dual boot machine and currently accessing the internet via XP.

Obviously, the line 'svn co [http://.](http://.)..' wont work because the internet isn't yet working!!

I have tried copying the files directly from that online directory to a local folder but the instructions after the point don't work either.

Entering 'make' at the command line just returns an error message stating that it needs more info.  I think it wanted a source file and a rule.

'sudo make install' just wanted a rule.

I am a total noob to linux but am eager to give it a shot.  This is an easy $5. Please help.

Thanks.

---

### Post by scenkner on 2008-08-13
Ok, nobody knows the answer. Offer is off the table till I come back.  I let you know if the offer is back.

---

### Post by Ayuthia on 2008-08-13
> **scenkner said:**
> 
Now do the following in a terminal:

svn co [http://synce.svn.sourceforge.net/svnroot/synce/trun](http://synce.svn.sourceforge.net/svnroot/synce/trun)

Since you have a working internet connection in Windows, why not just install subversion in Windows and check out the files there.  You can then copy the files over to Ubuntu and compile the code there.

---

### Post by chili555 on 2008-08-13
Linux in general and this forum in particular are all volunteer armies. We are not only not motivated by $5 but many of us are offended. Please refrain from money offers.

We are motivated quite highly by one thing, a thing that will motivate us to spend hours and days of hair-pulling, teeth-gnashing and nail biting time solving your problem. It is this: 'Thank you for your help.'

By the way, at my meager usual daily rate, $5 will get you about seven minutes. As you can see by my posts, I have thousands of minutes invested here; all free.

---

### Post by scenkner on 2008-08-13
chili555:

I do apologize if I offended anyone.  I know that $5 bucks is esentially pointless.  But I have very little hair left to pull out and I really just want to get it working.  I imagine that this is quite simple to someone with experience and I was hoping that I could get some help quickly with the offer as I have already spend hours working on this. Again, I am sorry if I offended anyone.  I just thought of it as a "donation".

Ayuthia:

I have already downloaded the files in that directory and stored them in a local directory via firefox.  Is it necessary to D/L them via subversion?  I have access to these files in linux, but the entries 'make' and 'sudo make install' just dont seem to work.  I am sure that I am missing some basic concept here.

---

### Post by scenkner on 2008-08-13
If a friend offered to come to my house and help me with my computer.  I would make sure to offer him a beer to repay his kindness.  I realize my wording in the initial post made it sound like I wanted to buy someone's services, but I was just hoping that i could get some quick help.  Thanks for your replies and I hope that I have not ruined my good name.

---

### Post by chili555 on 2008-08-13
Please let us have a link to the file you downloaded so we can help figure out how to install this.

I am not too familiar with synce, but I woner if this might help: [http://ubuntuforums.org/showthread.php?t=817090&highlight=synce](http://ubuntuforums.org/showthread.php?t=817090&highlight=synce)

---

### Post by Ayuthia on 2008-08-13
> **scenkner said:**
> 
Ayuthia:

I have already downloaded the files in that directory and stored them in a local directory via firefox.  Is it necessary to D/L them via subversion?  I have access to these files in linux, but the entries 'make' and 'sudo make install' just dont seem to work.  I am sure that I am missing some basic concept here.

I am not for sure about the difference between downloading the files instead of using subversion.  Mainly because I have not spent any time to see how subversion works.  Usually if you do a 'make', there is usually a makefile in that directory.  If there isn't, make doesn't work.

It looks like their site also has packages to download instead of using subversion ([http://sourceforge.net/projects/synce](http://sourceforge.net/projects/synce)).  Have you tried those?

As chili555 said, it would be helpful for us to know what files you have downloaded so that we can help figure it out for you.

If you and your friend still have problems, just come back and let us know where you downloaded the files and what steps you have done.

---

### Post by scenkner on 2008-08-13
The files I downloaded are here:
"https://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite"
They are currently in /Documents/usb-rndis-lite
The instructions that I am trying follow are here:
"http://blog.linuxoss.com/2008/01/howto-usb-internet-sharing-with-linux-and-wm6/"
similar to this:
"http://ochsenhirt.org/2008/05/20/use-internet-connection-sharing-on-wm6-with-hardy-heron-howto/"

It seems that alot of people have had success with these instructions according to the responses.  Thank you for your help.

---

### Post by flytripper on 2008-08-13
ics through a smart phone is dumb . have you even inquired about the carrier costs? $6 a MB in England and thats cheap.

---

### Post by scenkner on 2008-08-13
flytripper, I dont understand. Carrier Costs?  I have unlimited MB Data usage for my phone.  Flat monthly fee.  This is at no additional cost to me as I need the Data plan for work.

---

### Post by scenkner on 2008-08-13
Im at work so Im working off my memory, but I think that I may have just figured this thing out.  Kbuild and Makefile have no extension at all, but I think that I remember seeing a .txt on these files.  Windoze may have appended them automatically. (I sure didn't do it.)  Anyway I am definitely open for more suggestions, but I will check that when I get home.  I could be wrong.

---

### Post by flytripper on 2008-08-13
i would check it out if i were you.. jus t friendly advice.. i asked o2 where i am from and they told me using the device as a gateway was not the same as using the phone to browse the net.

---

### Post by ByteJuggler on 2008-08-13
> **scenkner said:**
> 
I have already downloaded the files in that directory and stored them in a local directory via firefox.  Is it necessary to D/L them via subversion?  I have access to these files in linux, but the entries 'make' and 'sudo make install' just dont seem to work.  I am sure that I am missing some basic concept here.

OK, the deal is like this:  The commands you've been given basically pulls some software directly from a version control system, and then compiles it, and installs it.  So, in order to be able to actually get the stuff from version control, you need the version control system (which is called "Subversion") client to be installed.  The command name for this is "svn" which is short for subversion but obviously wont work before the package is installed.  Once it is installed you pull the source as described, with the "svn" command.

Then need to then compile it.  For this, a compiler and other build tools are required.  The "build-essential" package will install all the neccessary compilers and build tools to allow you to compile C/C++ etc software.  One of the commands in the "build-essential" package is the "make" command which builds/compiles a software package using a specification file called a "makefile".  "make install" will attempt installing the compiled executables to standard locations.  

Now, you can obviously get the source whichever way you want and copy it to your box.  But we will need to get the "build-essential" packages onto your machine so you can compile and install your pacakge.  You can probably try to download them [here]("http://packages.ubuntu.com/hardy/devel/build-essential") and install them manually by double clicking them from the desktop (which should open them with GDebi) or by using the "dpkg " command from a terminal.

---

### Post by scenkner on 2008-08-13
ByteJuggler, thank you for clearing that up for me.  I had pieced some of that together, but that really helps to have it clearly described.

now, as far as the errors I get when trying to use make, it doesn't seem that it cant find the command, but that the command isn't finding the right information.  The errors were something along the lines of not finding the source file and not finding the rule.  I did cd to the folder containing the files.

At the very beginning I was able to successfully execute: sudo install build-essential.

Thanks for all your help.

---

### Post by Ayuthia on 2008-08-13
> **scenkner said:**
> Im at work so Im working off my memory, but I think that I may have just figured this thing out.  Kbuild and Makefile have no extension at all, but I think that I remember seeing a .txt on these files.  Windoze may have appended them automatically. (I sure didn't do it.)  Anyway I am definitely open for more suggestions, but I will check that when I get home.  I could be wrong.

You might want to download the tarball:
[http://synce.svn.sourceforge.net/viewvc/synce/trunk/usb-rndis-lite.tar.gz?view=tar](http://synce.svn.sourceforge.net/viewvc/synce/trunk/usb-rndis-lite.tar.gz?view=tar)
That might be easier than trying to download or use subversion.  The link should automatically download the tarball.  Just copy the file over to Ubuntu and extract it by doing the following from the Terminal:
```
tar -xvvf usb-rndis-lite.tar.gz
```
This will create a folder called usb-rndis-lite.  Just go into that directory and you should be able to 'make' the file.


The tarball will be easier to build if you grab it from Windows.  It is a compressed archive that should be easily extracted in Ubuntu.  Hope that helps.

---

### Post by chili555 on 2008-08-13
> something along the lines of not finding the source file Do you have *linux-headers-generic* and *build-essential* installed? It will be very hard to proceed without internet connectivity. I compiled and installed these without warning or error.

Incidently, in the tutorial, this part:> Create an /etc/sysconfig/network/ifcfg-rndis0 with the following contents:is written for a Red Hat or Fedora system. We speak Debian here, so, when you get to that point, we will help you adapt it.

---

### Post by scenkner on 2008-08-13
I just wanted to thank all of you for your help.  The problem was with windows appending the files with a .txt.  I am posting this through linux via wm6 ICS right now.  Thanks alot.

It looks like there is an official way to thank a member so it follows them on the board.  Can someone tell me how to do that?

---

### Post by ByteJuggler on 2008-08-14
> **scenkner said:**
> I just wanted to thank all of you for your help.  The problem was with windows appending the files with a .txt.  I am posting this through linux via wm6 ICS right now.  Thanks alot.

It looks like there is an official way to thank a member so it follows them on the board.  Can someone tell me how to do that?

Thank posters for useful posts by clicking on the blue ribbon button (bottom right) on the post.  :)

---

### Post by ByteJuggler on 2008-08-14
> **scenkner said:**
>  The problem was with windows appending the files with a .txt. 

<indignation>Don't you just love it when Windows "thinks" on your behalf. </indignation>

Glad you got it sorted anyway! :guitar:

---

### Post by chili555 on 2008-08-14
> <indignation>Don't you just love it when Windows "thinks" on your behalf. </indignation>+1000

What I *really* love is when Windows has been purged and banished forever from every one of the five computers in the house.

---

### Post by truckbbman on 2008-09-27
$30 for 6 gigs with Rogers in Canada

---

