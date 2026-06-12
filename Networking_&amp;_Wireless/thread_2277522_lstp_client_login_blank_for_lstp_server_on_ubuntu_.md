---
title: "lstp client login blank for lstp server on ubuntu 14.04 , what I'm missing here..?"
date: 2015-05-09
forum: Networking &amp; Wireless
---

### Post by aravinda2 on 2015-05-09
I am trying to configure a lstp server ( `ip of lstp server : 172.16.40.0` ) on a `64bit ubuntu 14.04` and check it network booting virtualbox vm (harddisk less vm) 
I configured everything according to this doc [http://ubuntuforums.org/showthread.php?t=2173749](http://ubuntuforums.org/showthread.php?t=2173749)


But when I enter root user and password in "virtualbox vm ltsp client", It boots perfect, authenticates perfect.. but not loading desktop.. I mean not loading unity kind of desktop.. just blank.. 




  [IMG]http://i.stack.imgur.com/X5OEe.png[/IMG]


Here are the things I did while configuring lstp server 


First Updated the server 


   ```
 sudo apt-get update && sudo apt-get upgrade

```

Then install LTSP, a proxy DHCP server, and a TFTP server: 


    s```
udo apt-get install ltsp-server dnsmasq tftpd-hpa

```

Client operating system image built using 


   ```
 sudo ltsp-build-client --arch i386

```

Then, to enable support for proxy DHCP by default i ran 


    ```
sudo sed -i 's/ipappend 2/ipappend 3/g' /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default

```

and here is my configured `ltsp.conf` at `/etc/dnsmasq.d/ltsp.conf`


    ```
#
    # Dnsmasq running as a proxy DHCP and TFTP server
    #
    # See: http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html
    #
    
    #
    # TFTP
    #
    
    # This might work instead of tftpd-hpa:
    #enable-tftp
    #tftp-root=/var/lib/tftpboot
    
    #
    # DHCP
    #
    
    # DHCP proxy on this network
    dhcp-range=172.16.40.0,proxy
    
    # Tell PXE clients not to use multicast discovery
    # See section 3.2.3.1 in http://tools.ietf.org/html/draft-henry-remote-boot-protocol-00
    dhcp-option=vendor:PXEClient,6,2b
    
    # Better support for old or broken DHCP clients
    dhcp-no-override
    
    # Enable this for better debugging
    #log-dhcp
    
    #
    # PXE
    #
    
    # Note the file paths are relative to our "tftp-root" and that ".0" will be appended
    
    pxe-prompt="Press F8 for boot menu", 3
    pxe-service=x86PC, "Boot from network", /ltsp/i386/pxelinux
    pxe-service=x86PC, "Boot from local hard disk"

```



Then restarted service `sudo service dnsmasq restart`


**(Tried without `/var/lib/tftpboot/ltsp/i386/lts.conf` and same result of above blank desktop when booting vm client.. )**




Then go ahead and edited, `/var/lib/tftpboot/ltsp/i386/lts.conf`


added 


   ```
 [Default]
    LDM_DIRECTX = True

```

then updated image and run the following 


    ```
sudo ltsp-update-image


    sudo sed -i 's/ipappend 2/ipappend 3/g' /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default



```**-----------------------------------------------------------------------------**


Please note: Since they have stated in the above tute " that on Ubuntu 14.04, there is currently a bug with tftpd-hpa" I edited `/etc/init/tftpd-hpa.conf` according to this [https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/522509/comments/40](https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/522509/comments/40)


and here is my `/etc/init/tftpd-hpa.conf`




    ```
# tftp-hpa - trivial ftp server
    
    description     "tftp-hpa server"
    author          "Chuck Short <zulcss@ubuntu.com>"
    
    #start on runlevel [2345]
    start on (filesystem and net-device-up IFACE!=lo)
    stop on runlevel [!2345]
    
    console output
    expect fork
    respawn
    
    env PIDFILE="/var/run/tftpd-hpa.pid"
    env DEFAULTS="/etc/default/tftpd-hpa"
    
    pre-start script
            if [ -f ${DEFAULTS} ]; then
                    . ${DEFAULTS}
            fi
    
            # Ensure --secure and multiple server directories are not used at the
            # same time
            if [ "$(echo ${TFTP_DIRECTORY} | wc -w)" -ge 2 ] && \
               echo ${TFTP_OPTIONS} | grep -qs secure
            then
                    echo
                    echo "When --secure is specified, exactly one directory can be specified."
                    echo "Please correct your /etc/default/tftpd-hpa."
                    stop
                    exit 0
            fi
    
            # Ensure server directories are existing
            for _DIRECTORY in ${TFTP_DIRECTORY}
            do
                    if [ ! -d "${_DIRECTORY}" ]
                    then
                            echo "${_DIRECTORY} missing, aborting."
                            stop
                            exit 0
                    fi
            done
    
    end script
    
    script
            if [ -f ${DEFAULTS} ]; then
                    . ${DEFAULTS}
            fi
            exec /usr/sbin/in.tftpd --listen  --user ${TFTP_USERNAME} --address ${TFTP_ADDRESS} ${TFTP_OPTIONS} ${TFTP_DIRECTORY}
    end script



```

**-----------------------------------------------------------------------------**


Rebooted the server as well , yet I'm stuck with blank screen as above..No matter if I keep it one hour , still its blank... What I'm missing here, ? any help would be greatly appreciated ..

---

### Post by UnhappyGhost on 2015-06-24
> **aravinda2 said:**
> I am trying to configure a lstp server ( `ip of lstp server : 172.16.40.0` ) on a `64bit ubuntu 14.04` and check it network booting virtualbox vm (harddisk less vm) 
I configured everything according to this doc [http://ubuntuforums.org/showthread.php?t=2173749](http://ubuntuforums.org/showthread.php?t=2173749)


But when I enter root user and password in "virtualbox vm ltsp client", It boots perfect, authenticates perfect.. but not loading desktop.. I mean not loading unity kind of desktop.. just blank.. 

.


Here is a Sample lts.conf file in case you need to edit anything. Look at the lines that are bold and uncomment the line for gnome-fallback and see if it loads the gnome-fallback in the clients.


unhappyghost@unhappyghost:$    sudo nano /var/lib/tftpboot/ltsp/i386/lts.conf


[default]
#  X_COLOR_DEPTH = 24        # to set the color depth on display
#  LOCALDEV = True            # use local hardware on clients
#  SOUND = True            # use sound drivers on clients
#  NBD_SWAP = Y            # use swap to be set on server
#  SYSLOG_HOST = server    # use server as syslog_server
#  XKBLAYOUT= en            # keyboard default to en
#  SCREEN_07 = rdesktop
#  RDP_OPTIONS = "-a 16"
#  RDP_SERVER = 192.168.5.99    # IP Address of the Windows Terminal Server with AD
#  LDM_ALLOW_GUEST = True # enable guest logins, for old edubuntu
#  LDM_GUESTLOGIN = True  # enable guest logins, for newer edubuntu
# LDM_THEME = edubuntu     # set theme folder - edubuntu, ltsp, default
  LANG = en_US.UTF-8         
  LANGUAGE = en_US.UTF-8
  LDM_LANGUAGE = en_US.UTF-8
**#  LDM_SESSION = "gnome-session --session=gnome-fallback"   #For Ubuntu Gnome Desktop!!!**
**#  LDM_REMOTECMD = /usr/bin/startkde              #For Ubuntu Unity UI Desktop!!!**




ctrl+O to save the changes
ctrl+X to exit nano editor

after the changes to the lts.conf file you have to issue the below mentioned ltsp-update commands after every change
Also you mentioned that it authenticates but the desktop doesn't load, so the sshkeys may be the problem.


unhappyghost@unhappyghost:$   sudo ltsp-update-kernels
unhappyghost@unhappyghost:$   sudo ltsp-update-sshkeys
unhappyghost@unhappyghost:$   sudo ltsp-update-image

---

### Post by UnhappyGhost on 2015-06-24
Could you please share the configuration in the following files 
/etc/default/tftpd-hpa
/etc/dnsmasq.d/ltsp.conf
/var/lib/tftpboot/ltsp/i386/lts.conf

Am having trouble setting up the ltsp server and so may be looking at your configuration files and comparing with the ones i configured, i will be able to figure out where did i do wrong.

---

