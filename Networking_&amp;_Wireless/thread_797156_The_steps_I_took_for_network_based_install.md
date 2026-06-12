---
title: "The steps I took for network based install"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by mercman2000 on 2008-05-17
For Ubuntu 8.04

This is for installing over your own local network using an existing Ubuntu system.  You can task this to a virtual machine on the same network as I did.  The virtual machine served as the server in this scenario, and my Mini ITX box the client.  While that machine is on the KVM switch, it lacks a CDROM and floppy, but it can boot off the network.  That is what prompted this little writeup.

1. Manually configure your network device on the server machine.

2. Once manually configured, take any other DHCP daemons (router or otherwise) in your network offline so the client sending the DHCP request will get served by this particular machine.

3. Spawn a terminal now and get the packages I used to set this up.

3a. As root on the server: apt-get install tftpd-hpa apache2 dhcp3-server

4. After apt-get completes its run, dhcp3-server will probably fail to start, this is OK.  We'll fix this later.

5. Insert your Ubuntu CD (Alternate) into the drive.  I mounted the ISO on my Windows box in VMWare.

6. We're going to now make an ISO from this.  Execute cat /etc/fstab to show your filesystem table.

7. Locate the device entry for your CDROM drive containing the disc.  Mine is /dev/scd0 and was at the end of the file.

8. Make the ISO image.  As root, execute cat /dev/scd0 > /alternate.iso (or dd if=/dev/scd0 of=/alternate.iso works too)

9. Mount the ISO in your tftp boot directory (this is /var/lib/tftpboot)

9a. First, go into /var/lib/tftpboot and make a directory named ubuntu (cd /var/lib/tftpboot, then, mkdir ubuntu)

9b. Next, execute mount -o loop [source] [destination].  I ran mount -o loop /alternate.iso /var/lib/tftpboot/ubuntu

9c. Check your results.  The expected result here is that you can go into the ubuntu directory, and you will see files such as cdromupgrade, md5sum.txt, README.diskdefines, and directories such as dists, install, pics, preseed.  More will be present, but if you're able to see these things, everything went well.

10. Now the ISO is mounted, since this is served over HTTP, we need to tell the Apache server where to find those files.  We're going to do this through a symbolic link.

 10a. Go into /var/www: cd /var/www

 10b. execute ln -s /var/lib/tftpboot/ubuntu/

 10c. execute ls -l to check your result.  The expected result here is that you see an entry in the ls output that reading like "ubuntu -> /var/lib/tftpboot/ubuntu" on the right side where the directory is listed.  To further check your result, you can go into the ubuntu directory (from /var/www, execute cd ubuntu) and get a listing of files.  You should see the same thing observed in 9c.

11. Now we're going to make the DHCP daemon work.  The configuration file is stored in the /etc/dhcp3 directory and is named dhcpd.conf.

 11a. Even though it is broken and cannot start now, it is always a good practice to make a backup.  First execute cd /etc/dhcp3, then execute cp dhcpd.conf dhcpd.conf.backup

 11b. Open dhcpd.conf in your favorite editor.  If you don't have one, let's use gedit.  execute gedit dhcpd.conf &

 11c. Now, configure the file.  I leave this part entirely up to you, but for sake of example, here is what I configured for mine:

ping-check = 1;
filename = "ubuntu/install/netboot/pxelinux.0";
subnet 192.168.1.0
netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
option domain-name-servers 192.168.1.1;
range 192.168.1.220 192.168.1.230;
}

 11d. After configuration, save and close that file.  Now we're going to restart the DHCP server.  Execute /etc/init.d/dhcp3-server restart

Expected output is:

 * Stopping DHCP server dhcpd3 [fail]
 * Starting DHCP server dhcpd3 [OK]

(There will be more space seperating the status messages from the action messages)

12. Believe it or not, this is all finished!  Boot your client for the first time and if all went well, it should boot over the network.

We're done dealing with the server, the next steps deal with the client setup.

13. You're prompted to boot now, hopefully.  Go ahead and press enter, this will take you into getting the setup going for this.

14. Follow the prompts as you need to until you get to the point of the setup page for "Choose a mirror of the Ubuntu archive".  Go to the top of the list here and select "enter information manually"

15. First, you're entering the hostname.  This wasn't working too well for me, because the Ubuntu system I started all this on is a VMWare system.  While it should have registered its name with the local DNS server it didn't.  That is why I did the manual configuration in the beginning so I would know the IP address and not need to worry about what IP got leased.  I just used the IP 192.168.1.200 (The server machine IP)

16. I kept the default archive mirror directory of /ubuntu/

17. Proxy info was left blank

18. Now, it loads up the components, you're prompted to configure the timezone.... and the install goes from there, all taking place over the network.

I'm now fully installed on the ITX machine with 8.04 and my install went great, no problems booting up or anything like that.

To deal with a reboot on the server, I think you only need to remount the ISO image from /var/lib/tftpboot into the ubuntu directory created earlier.

I hope this is able to help someone with a local network install... I documented as I went along and cleaned it up afterwards to make it a bit more user-friendly.

---

