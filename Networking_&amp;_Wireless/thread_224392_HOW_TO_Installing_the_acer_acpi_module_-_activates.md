---
title: "HOW TO: Installing the acer_acpi module - activates wireless on Acer laptops"
date: 2006-07-27
forum: Networking &amp; Wireless
---

### Post by ovimunt on 2006-07-27
***Last updated on 29/07/2006 21:05 GMT.***

**ATTENTION: This HOW TO covers ONLY the installation of the *acer_acpi* module and NOT of the wireless adapter drivers.**

Before you can go ahead and install the ***acer_acpi*** module you need to make sure you have some other tools installed.
```

sudo aptitude update
sudo aptitude install build-essential

```

***UPDATED:***
You'll also need the linux headers:
```

sudo aptitude install linux-headers-$(uname -r)

```
***END OF UPDATE***

Once this is done you can go ahead and install the ***acer_acpi***.
First you should create a folder to keep all your downloads in one place.
```

mkdir /home/USER_NAME/download

```
Where USER_NAME is your actual user name.

Now go to the new folder
```

cd /home/USER_NAME/download

```

and download and install the package:
```

wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar zxvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
make
sudo make install
cd ../..

```

Load the acer_acpi into memory and activate the wireless:
```

su
modprobe acer_acpi
chmod 777 /proc/acpi/acer/wireless
echo "enabled: 1">/proc/acpi/acer/wireless
exit

```

And check if it worked:
```

dmesg | grep acer_acpi

```

You should get some output like this:
```

[17179594.992000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17179595.000000] acer_acpi: Wireless value 1

```

Right, this might have worked for now but you need to load and activate ***acer_acpi*** every time your computer starts. 
For this you can write a little start up script so you don't have to do it manually each and every time.

[b]ATTENTION!
For Gnome type:[/b]
```

sudo gedit /etc/init.d/acer_acpi_wireless_enable

```
**Or if you're running KDE type:**
```

sudo kate /etc/init.d/acer_acpi_wireless_enable

```

Paste the following code and save:
```

#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi

                chmod 777 /proc/acpi/acer/wireless

                echo "enabled: 1" >/proc/acpi/acer/wireless

                ;;

        stop)

                echo "enabled: 0" >/proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac

```

Make the file executable and add it to the appropiate linux run levels.
**ATTENTION! Don't miss ANY of the characters in the following lines, especialy the dots in the third line!**
```

su
chmod 755 /etc/init.d/acer_acpi_wireless_enable
update-rc.d acer_acpi_wireless_enable start 39 S . start 34 0 6 .
exit

```

Now check if it worked:

```

ls /etc/rcS.d/S39acer-acpi-wireless-enable
ls /etc/rc0.d/S34acer-acpi-wireless-enable
ls /etc/rc6.d/S34acer-acpi-wireless-enable

```

If you get any ***No such file or directory*** messages then something must have gone wrong during the last couple of steps but your ***acer_acpi*** is still installed and can be started manually if needed.

If you didn't get any error messages everything should be up and running. You can now restart the computer and, if you have already installed the wireless drivers, your wireless adapter should work fine and be ready to configure.

---

