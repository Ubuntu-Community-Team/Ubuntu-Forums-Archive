---
title: "Networking Ubuntu computers?"
date: 2018-03-22
forum: Networking &amp; Wireless
---

### Post by david-buck on 2018-03-22
Hello, I have recently started using Ubuntu (versions.14;16 & 17))  on several old PCs and been very impressed by the way it automatically  sets itself up and communicates with any peripherals attached.  I have  had no problem getting on line and within 30/40 minutes of starting can  be running BBC News videos and sending emails.  However the one thing I  still havent mastered is simple file sharing on a local network between 2  Ubuntu PCs!  I can ping the router ok and connect to the internet and  send emails from both but cannot get them to 'see' each other and share  files!  I have tried setting up fixed IP addresses on each and created  "ethernet network1" alongside "wired network1" (I do not use wifi -  wired connections through switch on one computer).  Under 'Networks' i  get a listing of "Windows Network" and "dp-72830370" but clicking on  either simply gives an "Unable to access location" error message!  Where  am I going wrong this has always been a pretty straightforward task on  any version of Windows I have used?  Has anyone else had such difficulty  in networking for file sharing when every else seems to work smoothly?!

Thanks in anticipation of some solution,
DB

---

### Post by TheFu on 2018-03-22
Windows announces CIFS shares on the network via broadcasts.  This doesn't scale to larger networks.
Unix systems work differently. Expecting them to work like Windows will just lead to frustration.  

So ... there are many different ways to make storage available between Unix systems. You have choices to make.
* **ssh-based** access.  this can be using almost any file manager with either sftp://  or ssh:// in the URL. All ssh connections will honor ssh-keys, if you create them and set them up. ssh is how Unix systems are administrated and how power users communicate between systems, routers, managed switches, android, OSX, .... everything except Windows.
* **NFS** - this is a server-to-server shared storage method.  File permission and directory permissions and ownership including group stuff all works with a tiny bit of setup.  This is NOT user-to-server.  This is server-to-server to each server AND each client needs to be configured by the administrator of each system.
* **CIFS** - this is the protocol that MS-Windows uses. It is user-to-server and doesn't honor native Unix permissions.  For each system you want to setup "sharing", then you'll need to setup and configure CIFS via **Samba**. Samba effectively ignores Unix permissions, which is a bad thing if all the systems are Unix.

ssh, scp, sftp, rsync-over-ssh are all considered secure enough for use over the internet.

nfs is for LAN-only use.  It is faster than the other choices.  NFS mounted storage looks like a local disk when mounted.  You can treat is like local storage too.  All ownership, groups, and permissions are maintained ... except root is ignored for all NFS-client requests.  Root/sudo can be used as normal on the NFS server for the local storage, just not from an NFS-client (without a setting that drastically reduces security).

CIFS is what you want if you have Windows computers and want to share storage with them.

Linux isn't Windows.  NFS is extremely stable once setup.  Generally, you'll never need to worry about it again, unless the NFS server is off.  There are ways to gracefully handle that too, but they are a little more complex than someone new-to-Linux likely wants to deal with.  Not hard, just a few steps.

For Samba services to be "seen" on the network, there is an nmbd tool ... it is a broadcast/announce thing and automatically runs after you've setup samba. Generally, we don't think about it anymore and I can't remember any issues with nmbd since the 1990s.
There is also **avahi** which helps different services announce they are available on a LAN. I think it uses the ZeroConf protocol.  I've had issues with it for years, so I remove it from all installs fairly soon.  Did a fresh install 2 weeks ago and avahi got in the way.

Oh ...**WinSCP** is an sftp client for Windows. Full drag-n-drop explorer-like interface.  There are sftp clients for every networked OS that I know.  Android has a bunch of options.

And lastly, if you have setup samba sharing (or attempted to do so) using any GUI at all, beware that the GUI methods tend to be much slower than if you do it manually with the /etc/samba/smb.conf file.

So you have some choices to make.  
I use sftp when I'm away from home and want access to a few files. Nautilus, Thunar, Caja, are some different Linux file managers that I know support it.  I suspect others all do too.
I use NFS in the house for all Unix-to-Unix file sharing.  There are 3 NFS servers and about 7 NFS clients.
I use CIFS on 1 Linux machine that gets edited video files from Windows. It is easier and faster than using WinSCP. 

Setting up ssh/sftp/scp is pretty bonehead and will get you started in 5 minutes. If you want to use hostnames and not IP addresses, then you'll either need to use a DNS server or setup the /etc/hosts files for each computer to know about the other computers. For 3 systems, it wouldn't be hard.  Just add 3 lines to the bottom of the file with the 192.168.x.x IP and names for each.   Plus having ssh access is very handy if/when there are GUI issues.  You'll be able to ssh in if the GUI locks up and do some troubleshooting.  The GUI on Linux is just another program.  Chances are that if the GUI becomes unresponsive, the OS is still 100% fine underneath.

Getting CIFS/Samba working well is a little harder and I'm NOT an expert. I've been using it since the mid-90s and set it up for businesses a few times, but newer versions seem to be a little more complicated to replace MS-Active Directory.  I haven't run into that yet.

---

### Post by david-buck on 2018-03-23
Many thanks for such a comprehensive reply - most helpful!  I used Unix on  'main-frames' many years ago (CLI for SPSS stats package was something  to behold?!), I guess my expectations for an automatic connection came from the ease with which Ubuntu has set itself up with all my other peripherals etc. in such a short time.  

Since my needs seem to be closer to your "use (of) NFS in the house for all Unix-to-Unix file sharing".  Can you point me to a help page which can tell me how to do this step by step for a newbie?
Many thanks,
DB

---

### Post by oldfred on 2018-03-23
I find this a bit complex.
       [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)
Autofs mount directories on an as-needed basis.
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) 

Much better even if very old:
[https://ubuntuforums.org/showthread.php?t=249889](https://ubuntuforums.org/showthread.php?t=249889)

My example similar to above:
I only mount when I want to copy from my laptop to my desktop, or occasionally from one desktop to another. So I run scripts to make system I am on connect.
I set up all systems with server software.

I install regularly, but use the current LTS as main working install. But created scripts for new install.

Part of one of install scripts is to install software I want:
 apt-get install nfs-kernel-server nfs-common rpcbind
dpkg-reconfigure rpcbind
exportfs -a 

Another script includes configuration including NFS, if just doing once, you can copy & paste entry into exports with your mount folder(s):

   fname_exp=/etc/exports
nfs1="/mnt/data   192.168.1.0/24(rw,no_root_squash,async)"
nfs2="/mnt/backup 192.168.1.0/24(rw,no_root_squash,async)"
nfs3="/home/fred  192.168.1.0/24(rw,no_root_squash,async)"
#nfs1="/mnt/data   192.168.1.0/24(rw,no_root_squash,async)"
#nfs2="/mnt/backup   192.168.1.0/24(rw,no_root_squash,async)"
echo $nfs1 >> $fname_exp
echo $nfs2 >> $fname_exp
echo $nfs3 >> $fname_exp 
   
You can add mounts to fstab if remote system always connected, but mine are not so I run another script to mount:
# ! not 
if [ ! -d /mnt/data_DT ]; then

  mkdir /mnt/data_DT 
 fi    # ! not 
if [ ! -d /mnt/backup_DT ]; then

  mkdir /mnt/backup_DT 
 fi    # ! not 
if [ ! -d /mnt/home_DT ]; then

  mkdir /mnt/home_DT 
 fi   
  sudo mount 192.168.0.20:/mnt/data /mnt/data_DT
sudo mount 192.168.0.20:/mnt/shared /mnt/backup_DT
sudo mount 192.168.0.20:/mnt/data /mnt/home_DT 
#sudo mount 10.0.0.2:/mnt/data /mnt/data_DT
#sudo mount 10.0.0.2:/mnt/backup /mnt/backup_DT
#sudo mount 10.0.0.2:/home/fred /mnt/home_DT 

With different routers/vendors some routers were 10.xxxx and others 192.xxx, so I comment out old just in case I change again.
Both systems have /mnt/data as main data partition, so I have to create new similar mount, so I know which is which.
And 192.168.0.20 is address of other system.

---

### Post by TheFu on 2018-03-23
While oldfred's scripts look like they will work, I use **autofs** to manage active NFS mounts and find it works well.  It is much easier to me and I would highly recommend that oldfred switch to using it.  NFS doesn't need to be hard.  For example, on my laptop, I don't have to do anything when I'm on the home network ... the nfs storage is just there and available.  The access of the storage alone is sufficient to cause the mount.  As long as it is actively used (a bash pwd is sufficient), then the mount will remain.  If it isn't actively used, after 5-10 minutes, then that mount is released.

The other links for NFS setup is what I would have provided.  That isn't to say that others won't work, just that I haven't needed to look for a how-to and use it for NFS in about 20 yrs. 

When I'm NOT on the home network, I just don't cd/use the nfs storage and everything is fine.  

Many of the how-to guides try to address lots of options and possible requirements.   It really comes down to setting up the server on the server-side, then setting up the client on the client-side.   There are lots of details that can trip up someone new to networking and most guides will skip over name resolution stuff.  They (and I) would assume you have that working already since every network must have that infrastructure solved already.

I'm terrible at helping new people to Linux.  It is my failing. Sorry.  I'm great at broad ideas and keywords to help you do research on your own, but if you need to know exactly what to type - I cannot help. Trivial details/issues that you are likely to run into won't be something I've seen just because of the way I pre-handle most of those as part of my system installation processes.  Like IP name resolution.  I solve that BEFORE doing any install.  Then I just need to hook up that single,new,system to the my infrastructure DNS. All the other systems already know about the new box, so to/from connections by-name "just work."

Did you setup ssh on all the machines yet?  Regardless, that really is the first step - well, after making certain that each system has a static IP and can ping each other by-name.  If you post that information with the source directories you want to share and the client-side locations you want them to appear, then the autofs stuff can be crafted for you specifically - it is only 1 server-side file and 2 client side files to solve it.  Basically, 1 line to each file will do it. 
server-side: /etc/exports
client-side: /etc/auto.master and /etc/auto.nfs
Easy, peasy.  Restart the server after any change to "exports" and restart autofs if you change master or .nfs files.  Active mounts are not impacted.

And there is always the manpages. Manpages are awesome for this stuff when you don't have an example already to work from.

---

### Post by SeijiSensei on 2018-03-23
For just two machines you might want to consider [**SSHFS**]("https://help.ubuntu.com/community/SSHFS#Command-line_Usage").  It's pretty easy to implement.  I believe most Ubuntu distributions come with the openssh-server package installed by default, but if not, you can install it, and the sshfs package, like this.  (Do this on both machines.)
```

sudo apt install openssh-server sshfs

```
Let's suppose that computer A has IP address 192.168.1.1, and computer B has 192.168.1.2.  Let's mount your home directory on A to the directory /home/david/remote on computer B.
```

mkdir /home/david/remote
sshfs david@192.168.1.1:/home/david /home/david/remote

```
You will be prompted for your password.  (You can avoid being prompted by using SSH "[keys.]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")")  Follow a similar procedure on computer A.

If you want to connect to the root of the remote filesystem, that's a bit trickier to do with Ubuntu for [security reasons]("https://help.ubuntu.com/community/RootSudo").  If you can transfer the files you need by copying them into your home directories, then this approach should be fine.

---

### Post by Morbius1 on 2018-03-24
It's been a while but shouldn't there be a ":" between the ip address and the path to the folder:
> sshfs david@192.168.1.1[COLOR=#b22222]**:**[/COLOR]/home/david /home/david/remote

---

### Post by TheFu on 2018-03-24
Yep.  sshfs uses scp/sftp/rsync URLs - though rsync also supports the double-colon method.
sshfs is pretty handy sometimes, but I think it is the slowest of all the options.

For most people, using nautilus with sftp://{IP}/ would be the easiest.  I know caja (default Mate file manager) works with sftp:// as well.  Technically, sftp is the protocol, but some file managers allow/require ssh:// for some reason. [https://askubuntu.com/questions/464543/how-do-i-use-sftp-within-nautilus](https://askubuntu.com/questions/464543/how-do-i-use-sftp-within-nautilus)

---

### Post by SeijiSensei on 2018-03-24
> **Morbius1 said:**
> It's been a while but shouldn't there be a ":" between the ip address and the path to the folder:

Yes, sorry!  Corrected.

I don't think speed matters much in situations like these.  We're talking about helping a novice user find an easy-to-implement solution for simple file sharing between two machines.  Why go to all the hassle of Samba or NFS for a task like this?

---

