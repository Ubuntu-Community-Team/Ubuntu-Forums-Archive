---
title: "vmware sharing folder with xp and gutsy"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by larryfroot on 2007-12-13
Hi, there is more than one way to do many things, and setting up a shared folder between vmware server and ubuntu is no different. But you might like to try the following...I found it to be a really excellent tutorial.

I found these instructions to be clear, sound and effective in getting the vmware server with xp as its guest to share a folder in my home/username directory (which is in a gutsy install).

I am really impressed by this guys work as I am an absolute newbie to networking and was wondering what the hell hit me as I bimbled around the forums watching people use a strange terminology that I had never had cause to be interested in before. But then I came across this and did the job. So I am no longer merely a newbie. I am now a grateful newbie. Anyways here is the link...

[http://http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/]("http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/")

....but there are a few things to watch out for. Firstly...(please remember I am coming from a newbie stance here, and there may be other newbies reading this)...when asked to ping your IP address (a series of numbers similar to 179.35.18.1) that you will be allotted by vmware in order for other machines including the host &#8211; your ubuntu installation &#8211; to contact xp through, simply open up a dos prompt in windows and type ping <the.ip.address.here> then press enter.

If it returns a response time, then you are in business. if not then return to the series of ip addresses that vmware has thrown in your direction until you enter in the right one.

Secondly be clear about the type of connection you want. In guest settings in vmware there are three options given, each with a clear explanation of what each option is about. So before anything else, choose your type of networking from here. To attempt say. a host only network  whilst chucking in the requirements for a NAT network on the Linux/Samba side is counter-productive to say the least. 

When you have success, then please remember, before logging into your shared folder, that samba needs to be running in linux. An odd one this, as samba is down in my services as starting automatically, but I once had to start it manually in order to access my shared folder from xp. Command line stuff needed to make sure everything is nice and fresh in samba land is sudo /etc/init.d/samba restart Or sudo /etc/init.d/samba start I will leave you to work out how to stop samba if you need to. You will need samba running to use your shared folder xp side. 

Finally permissions. You may find that files and folders are locked down when you try to access them from xp. This is because the group and/or user you created for the purpose of running samba and setting up a shared folder hasn't permissions to read or change files made by you as username:usergroup. A quick right click on the affected folders in Linux and changing permissions in the permissions tab will see you right. No sudo needed here as the samba user was created by username, so username has full command over the permissions for the samba user:usergroup settings. 

Lastly, vmware has given me a chance to evaluate xp and Linux together. There is absolutely no contest. In fact, I removed the 'Made for XP' sticker off my machine and stuck it on the toilet. I must admit, there is a certain aptness in seeing it there.

---

