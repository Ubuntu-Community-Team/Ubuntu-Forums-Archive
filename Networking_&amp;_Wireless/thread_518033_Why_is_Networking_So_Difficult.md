---
title: "Why is Networking So Difficult?"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by blueflyt on 2007-08-05
Somebody help me please. I have a small business and needed to add some new PC's to our peer-to-peer network. I was convinced by someone that I should install Linux on them to save money. So I've got Kubuntu installed on two PCs. Everything works fine; I can surf the Net (even wirelessly), do everything I normally do on a Windows machine...except for sharing files between the two Kubuntu machines! Why is this so difficult with Linux? 

When I try to share my home folder (or a sub-folder) by right-clicking on the folder (and entering the appropriate root password), I get a message that says "SMB and NFS servers are not installed on this marchine, to enable this module the servers must be installed." 

Okay, fine. How do I do that? Why do I have to spend hours (literally) reading through these forums trying to figure out something as simple as file sharing when it should come pre-packaged out of the box? This is really aggravating. What adds to my aggravation is the fact that Linux/Ubuntu still requires archaic text-based editing of obscure files using obscure instructions to set up what should be simple tasks.  

Can someone please provide me with SIMPLE, BASIC, NON-GEEK instructions on what I need to do to share folders between two machines running Kubuntu 7.04? The funny thing is, I can see my Windows Vista box's on the network as well as my XP box's and browse the shared folders on those machines (although only the XP machines will let me copy files). File sharing between the Kubuntu machines is the only show-stopper from keeping me from switching our other machines over to Linux eventually.  

Any simple, straightforward help will be appreciated. Please keep it simple: I don't appreciate people trying to impress me with techno-talk. Leave your ego behind. Keep it simple and you may just help a small service company with 11 employees switch over entirely to Linux/kubuntu, which would be a small, but, nevertheless, a great step in putting a chink in Microsoft's armor. 

Thank you in advance!

---

### Post by Sand Lee on 2007-08-05
Try these links:
 [https://answers.launchpad.net/ubuntu/+source/kdebase/+question/8421](https://answers.launchpad.net/ubuntu/+source/kdebase/+question/8421)
[https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/95452](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/95452)
I'm busy now, but I might be able to help later...

---

### Post by kesomir on 2007-08-05
using nfs or samba is the way to set up auto-mounted shares on the computers in a traditional file server setup, but you can use ssh to access files on one machine from the other quite easily as long as you have an account on the machine.

make sure ssh is installed by opening a console on each machine and entering the command

```
sudo apt-get install ssh
```

then, in konqueror type into the address bar:
```
fish://username:password@192.168.1.181/directory/
```

I use gnome so in nautilus it's ```
"ssh://192.168.1.181"
``` which; since I omitted the password and user, pops up a prompt box. I can't speak for the features in konq though.

NB: replace 192.168.1.181 with the actual IP or hostname of the machine you are connecting to.

---

### Post by ugm6hr on 2007-08-05
I'm afraid I'm not sure how the Kubuntu interface works - but if the menu is anything like Xubuntu / Ubuntu - there should be a Shared Folders entry somewhere.  If you just select that and follow the instructions, it's pretty obvious.mmIf you run a predominantly Windows Network - SMB (or Samba) is the most sensible mechanism, because it will fit right into your existing network.

My signature link (Easy Windows file sharing) below has an alternative method (designed for Xubuntu) if Kubuntu doesn't have the ability to browse network shares built-in (although I'm sure it does).

The most difficult part is passwords.  The easiest way is to remove the need for a password to access the Samba share. If you have security concerns re: this - then you can define the password with a command (but I can't remember how - smbpassword rings bells...) - but Windows tends not to use passwords to protect its shares as default either, so it probably won't be any different than the rest of the network.

Even if you don't use my technique - this bit is the part that opens passwords.  

> I then edited /etc/samba/smb.conf (as root) (in Terminal: gksudo thunar and browse and double-click file), and added just one line immediately below the [global] entry, so this part looked like:
```
#======================= Global Settings =======================

[global]
[COLOR="Red"]security=share[/COLOR]
## Browsing/Identification ###
The security=share removes all samba passwords to access the Ubuntu shared folders.
```

You *may* have to configure the Firewall, but that's easy with Firestarter (again an Ubuntu program available from Synaptic, but I think Guarddog is more Kubuntu orientated).

PS: *gksudo thunar* will not work in Kubuntu - you will have to use the Kubuntu equivalent (something like *kdesu konqueror* I think).

I hope that is helpful in getting you on your way.

---

### Post by bettyhills on 2007-08-05
I spent today searching similarly.

What worked for me:
Go to System -> Administration -> Shared Folders and click.

It will say Samba and NFS are not installed.  Tell it to install.

Then click Shared Folders again.  Add.  Choose the directory you want to  add to your home network.  **Be careful**.  Make sure that the other tab, the General Tab, contains the name of your Windows network if you already have one.  Then close.

I do not know what WINS server means and left it blank.

All your PCs should be able to see each other now.

---

### Post by blueflyt on 2007-08-06
SAND LEE:  Appreciate the feedback; however, providing a link to a page that is full of other links that have to be followed (which in turn takes one to pages with even more links) is not very useful.  There should be one place where a novice/beginner can go to find simple answers to basic questions.  More to the point, there should be somehwere in the Linux World that provides basic descriptions and answers.  For example, when would one use Samba vs. NFS?  (I know the difference, but that was after spending hours reading through different on-line forums.)  What are the underlying concepts behind each application?  Can both be run at the same time in order to access Windows vs. Linux boxes? Etc.  

KESOMIR:  Thanks for your straight-forward and articulate reply.  It's appreciated and you're one of the few that seem to be able to write instructions that are easily understood.  Nevertheless, and unfortunately, when I followed your instructions, I get an error message in Konqueror -- "An error occurred while loading fish://***: Could not connect to host ***" [Where *** is the name of the box I"m trying to connect to.]  

UGM6R:  There is a shared folders entry.  The problem is, when I try to set it up for sharing I get an error message saying SMB or NFS servers are not installed and it doesn't provide me with the option for installing them.  When I go to the package installation menu, there are no options for downloading and installing those applications.  Moreover, it appears that some SMB components are already installed.  

Yes, Samba would allow my Linux/Kubuntu boxes to fit right into the existing peer-to-peer network.  However, my whole reason for going down this path was to migrate away from Microsoft's world.  And I can't do that unless I/we are comfortable with all aspects (basic functionalities) of Linux/Kubuntu/Ubuntu.  Besides, half our Windows boxes are XP and the other half Vista.  File sharing works fine with the XP boxes, but Vista, while we can browse the folders, does not allow us to copy files (we get an error message during the copy process that says something to the affect, "File does not exist").  From what I've read in these forums, the Vista problem emanates from its more robust security.  

BETTYHILLS:  You wrote:  "What worked for me:
Go to System -> Administration -> Shared Folders and click.

It will say Samba and NFS are not installed. **_Tell it to install_**." [emphasis added]

The problem is, HOW do I tell it to install?  There are no options visible/available.  

TO ALL:  Thanks for your efforts and feedback.  Unfortunately, after spending a whole weekend at the office trying to get this initiative to work for my business, I'm throwing in the towel.  I think Linux/Ubuntu is great for people with a lot of time on their hands or, alternatively, Techie-types with a better grasp of programming.  It works great on stand-alone machines, and I'm sure it works in every other aspect.  However, I would never recommend this for small businesses, which usually have limited technology budgets.  Core functionalities, such as file and printer sharing are just far too convuluted for the average small business.  I'd rather spend a small fortune buying something that works out of the box than to download something free and then spend a large fortune in my valuable time trying to get it to work right.  

Best regards to all of you.  I'll check back in another year or two and see if things have progressed any further.  

Blueflyt

---

### Post by ugm6hr on 2007-08-06
Sorry to see that you were unable to get this to work.  Out of interest - was there a reason you chose Kubuntu rather than Ubuntu?  From the sounds of things - it is Kubuntu (rather than Ubuntu) that was the problem - since Ubuntu (and, interestingly, Xubuntu) are a lot easier to set up with shares (and automatically offer to install either/or/both Samba or NFS when you activate Shared Folders..

Have any other Kubuntu users found this to be an issue?

In case you want to give Ubuntu a go - this gives a clear video tutorial on how to do it on Ubuntu:
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by mips on 2007-08-06
All that was probably required was to install NFS&Samba via Adept or apt-get...

---

### Post by dfreer on 2007-08-06
The reason why bettyhills advice doesn't work is because there is a slight difference between [U]buntu and [K]ubuntu. The **Tell it to Install** is not in Kubuntu. The best thing to do here is to install samba and smbfs, which is required in order to *share* folders, although it is not needed to browse shared folders on other machines. This is why you can see other machines shared folders (don't quite know why it doesn't work with vista though).

So here's a short and quick way to share a folder, first by installing the packages:
```
sudo apt-get install samba smbfs
```

You can then share a folder by either right-clicking on the folder and selecting "Share Folder" or by going to the KDE Menu > System > Shared Folders.
Now, once you have a folder shared, you will need to add a username password to the samba server. This is akin to creating a new username/password, although if you wish you can use the same username/password as the one you use to login to the system. 
Create a new username/password with this command:
```
sudo smbpasswd -a *username*
```
Replace *username* with the user name you want to use. It should ask you for your **Password:**, which is your current system password, and then the **New SMB password:**, which is where you type the password you want to create for your new Samba user.

From that point, you should be able to access the share from a windows XP PC by navigating to Start > Run > //*Linux_IP_Address_here*/ and then type in the SMB username and password you just created. From a kubuntu machine, you should be able to reach it by Places > Remote Places > Add a Network Folder, and then fill in the required info. Note the SMB server is considered a **Microsoft Windows Network Drive**. Hope this helps!

---

### Post by adam15c on 2007-08-19
I share blueflyt's frustration. I am trying to rid myself of Windows. So far I have managed to set up my Desktop & Laptop with Ubuntu. On the Desktop things went very smoothly but on the laptop setting up wireless access to my Router has been a nightmare. Pages upon pages of links and instructions that work for one but not another. Anyway. This has been completed now.

However my problem is that I cannot access the files on my Desktop or vice verse with my laptop. I have printer sharing set up which works fine. I want to use ssh. Could someone give me a easy to follow tutorial? I don't need to access Windows, just Ubuntu to Ubuntu. I'm obviously doing something wrong, but what......?

I have opened Nautilus and tried to Connect to Server. Using the IP address I get Access Denied. Thanks.

---

### Post by BajaPaul on 2008-07-17
Thanks dfreer for cutting to the chase and answering the question.  I had the exact same problem.  You solution fixed it.

sudo apt-get install samba smbfs

Then just go to System Settings, Sharing, and it will set it all up for you.

It would be nice if Kubuntu would have just offered to install SMB and NFS since it needed it.  Come on developers, is that to much to ask?

We really shouldn't have to search the whole web to find soultions everytime we have a problem like linux often forces us to do.

BTW I am running Ubuntu and Kubuntu as a hobby project under Virtualbox on my 64-bit Vista Machine.  All works well.

---

