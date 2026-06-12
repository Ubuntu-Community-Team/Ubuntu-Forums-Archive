---
title: "File transfer between two machines running Ubuntu and using SSH"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by kagashe on 2008-03-14
I had successfully transferred a file from Windows machine to the one running Ubuntu through Samba but had no experience of a transfer between two Ubuntu machines.

I have an old desktop with 32 MB RAM on which Win98, Ubuntu server and Puppy Linux are installed. The CD drive on this machine still works. There is no USB port on this machine.

I have 3 years old Laptop on which the CD drive is not working and I don't intend to replace it.

Yesterday I was required to use some folders and files from a CD and decided to make an iso of the entire CD on the old desktop and transfer it to the Laptop by connecting the two machines.

For transferring the file I decided to use SSH, therefore I downloaded openssh-server on the desktop and installed it.

I made the iso using the dd command:
dd if=/dev/cdrom of=file.iso

I opened a Terminal on the Laptop and logged into the desktop through the command:
ssh desktopuser@ip_of_desktop

After confirming blah blah about RSA key etc I was asked the password and the terminal user changed as the desktopuser@desktop_host_name

I tried to transfer the file through scp command
scp file.iso laptopuser@ip_of_laptop:/home/laptopuser/

But found that the port 22 on the Laptop was closed.

I used the following command to see what was listening on the Laptop ports:
netstat -an | grep "LISTEN "

Although I was logged in from the Laptop to the Desktop no daemon was listening on port 22. I also changed the ssh client to openssh-client on the Laptop but could not make it listen on port 22.

I searched on Google but could not find any satisfactory solution.

Finally I decided to install openssh-server on the Laptop as well.

With openssh-server running on both the machine I could transfer the file that too after the server on the Laptop asked the password of the laptopuser.

Now my question:
Is it possible to transfer the file from the host which has ssh server to the host which has ssh client only on Ubuntu?

In other words how to make the ssh client listen on port 22?

kagashe

---

### Post by Oswald1 on 2008-03-14
I hope I'm not nitpicking, but I think the client would be named server if it was listening to some ports.

---

### Post by Zack McCool on 2008-03-14
The SSH Client doesn't listen.  Rather, try a different tact...

from your laptop:

```

scp desktopuser@ip_of_desktop:/home/user/Desktop/file.iso .

```

This requires the SSH server to be running on the desktop, but only the client to be running on your laptop.

---

### Post by kagashe on 2008-03-14
> **Zack McCool said:**
> The SSH Client doesn't listen.  Rather, try a different tact...

from your laptop:

```

scp desktopuser@ip_of_desktop:/home/user/Desktop/file.iso .

```

This requires the SSH server to be running on the desktop, but only the client to be running on your laptop.I had also tried this. Did not work. Following was the error:
> ssh: connect to host ip_of_laptop port 22: Connection refused
lost connectionI think for file transfer to take place ports on both machines need to be opened.

kagashe

---

### Post by handydan918 on 2008-03-14
> **kagashe said:**
> I had also tried this. Did not work. Following was the error:
I think for file transfer to take place ports on both machines need to be opened.

kagashe
The ssh daemon isn't such a resource hog that you can't use it on a lappy. If you're concerned about port 22 being open, install firestarter (or guarddog) and you can open port 22 as needed.

---

