---
title: "Triple Boot Query"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by jaycee23 on 2010-04-17
I have just added a second internal hard drive to my desktop. 

On the first drive I have Windows 7 and Karmic as a dual boot. It's all set up just as I like it and working well.

Now I have a second hard drive I would like to use it to test Lucid. I have split the second hard drive into two - one part to back up the main drive formatted as NTFS and the second part with 2 ext partitions, one for / and second for /home with a small swap area.

How do I install Lucid on the second hard drive so grub2 will give me the options to boot into windows / karmic or lucid.

PS. I expect problems with Lucid having an ATI graphics card so I would like to keep my Karmic partition completely separate until I'm happy with Lucid.

Thanks for your replies

:)

---

### Post by oldfred on 2010-04-17
Just be sure to use the advanced button on the last partition screen to choose where to install the lucid version of grub to sdb. Then in BIOS set sdb as the boot. It should find and let you boot everything, but if you want you can still boot from sda.

---

### Post by ajgreeny on 2010-04-17
Working on the assumption that at the moment you have grub on the MBR of sda, where your Windows 7 and karmic are, I think the best way to deal with the triple boot is to put your Lucid test install on the second disk, as you suggest, along with the NTFS backup partition, and then use one of two choices:-

1.  Simply let Lucid's grub take over the current grub, which it should do without problem, by allowing it to be installed onto the MBR of sda.  It should find both your current OSs, and they would be available to you from Lucid's grub.

2.  When you get to the final screen before you accept everything, and actually write to disk in the installation process, click on the Advanced button, at bottom right, and there choose to put grub on sdb, not one of its partitions but the disk itself.

If you choose to use option 1, Lucid will be the default boot OS, but you can still boot to Karmic and then change back to using its grub by running ```
sudo grub-install sda
```If you choose option 2, you will still have Karmic as the default boot OS, but can add Lucid to Karmic's grub menu by running ```
sudo update-grub
``` and once you are happy with Lucid, you can then change back to its grub in the same way, ie boot to Lucid and run ```
sudo grub-install sda
```once again, and then Lucid will become default OS.

I have more or less the same setup as you, but without windows, and 4 different OSs on my machine.  When I installed Lucid as the final of those, onto sdb, I chose to put its grub on sdb, and kept sda as first boot device with Karmic's grub used.

EDIT:
I could have explained it as simply as oldfred, above, but chose to add a lot more detail, which may help explain more about the way grub works and how to move from one grub to the other.

---

### Post by jaycee23 on 2010-04-17
Thanks for the replies.

AJGreeny - your assumptions are right

Ideally I want to be able to boot into windows 7 or karmic or lucid from the initial grub menu. Still a bit confused about what is the simplest way to do this. 

Also do I really need a swap partition for lucid? I do have 6GB of RAM

---

### Post by oldfred on 2010-04-17
I like to have a boot loader in every drive and an operating system on each drive that is booted from that MBR. I thought Ajgreeny explained the options a little more than my succinct/brief explanation.

If you do not hibernate you can use the same swap as your existing install. With 6Gb of memory you may never use swap unless you have lots of large applications loaded all at once or are doing video editing. With large hard drives additional space for swap does not use much of the drive and makes sure system is configured the standard way. I have seen a few with lots of memory say they do not have swap and it has worked ok - at least so far.

---

### Post by ajgreeny on 2010-04-17
> **jaycee23 said:**
> Thanks for the replies.

Ideally I want to be able to boot into windows 7 or karmic or lucid from the initial grub menu. Still a bit confused about what is the simplest way to do this. 
One of the great things about grub2 in comparison with legacy grub is that whatever is on your machine, a simple ```
sudo update-grub
``` will get it into the grub menu.  In legacy grub that had to be done by manual edits, easy enough once you sorted out the disk nomenclature, but still another thing that gave the chance of errors.

The main thing to consider is that whichever OS is providing the grub menu, that will be the default OS which is booted to, but as I said, you can change the grub used by using the command ```
sudo grub-install /dev/sda
``` from that particular OS, or simply by changing the disk which is first boot device in the BIOS.

---

### Post by undecim on 2010-04-17
Since you already have a working Ubuntu installed, make sure you use the "Advanced" button on the last step of the installer and make sure you don't install a bootloader.

Then, in your old Ubuntu install, run "sudo update-grub"

---

### Post by jaycee23 on 2010-04-18
Thanks for the replies - will try once I get some time. 

Seems like it may take a while to get things right.

Also is there anyway I can just get the three boot options on the boot screen ie Windows 7, Karmic and Lucid without all the other stuff that usually appears.

---

### Post by oldfred on 2010-04-18
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jaycee23 on 2010-04-18
Looks like I've got some reading to do!

Just a bit worried I might bork the system

---

### Post by jaycee23 on 2010-05-02
Sorry to take so long to reply but I've been having a few issues!!

As instructed I installed Lucid on sdb and placed its grub on sdb and changed sdb ti be the initial boot HDD. However although this worked to give me a triple boot system using Lucid's GRUB I intermittently lost my wired internet connection - it seemed as if no power was being supplied to the LAN port - router working fine! 

When I changed my initial boot HDD back to sda and used Karmic's GRUB I saw Lucid as a boot option but when I ran update-grub I got an error complaining of issues with device.map.

When I checked it with
```
cat /boot/grub/device.map
```I got ```
(hd0)    /dev/sda
```Then ran 
```
sudo gedit /boot/grub/device.map
```and manually added
```
(hd1)      /dev/sdb
```Now update GRUB works fine in Karmic,

However if I switch back to using sdb as primary boot HDD I still have problems with the LAN port. This does not seem an issue if I boot using sda.

Any thoughts welcome

---

### Post by oldfred on 2010-05-02
Since you have triple boot, are you booting the same version with sda as sdb? You may want to start a new thread with the intermittent internet problem as that is totally different and a new thread may get responses from those who know that better.

---

### Post by jaycee23 on 2010-05-02
To clarify - sda boots into karmic and sdb boots into lucid. So grub 1.97 beta on sda and grub 1.98 on sdb. Also when I boot into sda, the grub entry for lucid is extremely lengthy with a lot of stuff written after the kernel version. Any idea why? Also any explanation why I had problems initially. I know I've sorted it but would like to understand why it happened in the first place.

I'll leave the Ethernet issue for the moment.

---

### Post by oldfred on 2010-05-02
When you have multiple systems the menu can get very large. You should only keep 2 kernels (delete in synaptic) but I modified logic to only show 2 so I do not have to houseclean all the time. I copied only the entries I wanted into 40_custom so I could edit at will.

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

---

### Post by jaycee23 on 2010-05-03
Again further clarification
When I run
```
sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2
```I get
```
karmic 2.6.31-21
Windows 7 (loader) (on /dev/sda1)
'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb5)
'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb5)
```I've used drs305 guide

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

to change the karmic entry but am unsure why the lucid entry looks so different so have not tried to change that yet. What does the bit after "Ubuntu, with Linux 2.6.32-21-generic" refer to and is it safe to alter using drs305 guide?

---

### Post by oldfred on 2010-05-03
Since all the entries at the bottom are from osprober I would just copy them into 40_custom and edit at will. Then if they still work turn off osprober so you do not have double entries. If you ever add another system you can temporarily to prober on the find new settings. 

Of course if kernels get updated you then have to manually update entries. Or you can change entry to use the linked files vmlinuz and initrd in the /boot directory. With every kernel update they are updated with new link to that kernel.

linux /vmlinuz root=/dev/sdXY ro
initrd /initrd.img

the kernel versions are only required when using a separate boot partition

---

### Post by jaycee23 on 2010-05-05
Trying to install lucid's grub onto sda.

To recap on sda is Win 7 and karmic and karmic's grub
sba is lucid and lucid's grub

Logged into sdb using Lucid's grub then
Tried

```
sudo grub-install sda
```but got
```
/usr/sbin/grub-probe: error: cannot stat `sda'.
Invalid device `sda'.

```Output of fdisk -l is

```
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x35433173

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12415    99620063+   7  HPFS/NTFS
/dev/sda3           12416      182401  1365412514+   5  Extended
/dev/sda5           12416       44032   253963521    7  HPFS/NTFS
/dev/sda6           44033      156111   900274536    7  HPFS/NTFS
/dev/sda7          156112      165348    74196171   83  Linux
/dev/sda8          165349      182311   136255266   83  Linux
/dev/sda9          182312      182401      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cd57c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12841   103145270+   5  Extended
/dev/sdb2           12842       36481   189888300    7  HPFS/NTFS
/dev/sdb5               1        6318    50749272   83  Linux
/dev/sdb6            6319       12724    51456163+  83  Linux
/dev/sdb7           12725       12841      939771   82  Linux swap / Solaris
```What am I doing wrong?

---

### Post by srs5694 on 2010-05-05
> **jaycee23 said:**
> ```
sudo grub-install sda
```

You've got to provide the complete pathname. "sda" alone is the file sda in the current directory. "/dev/sda", OTOH, is the file sda in the /dev directory, and only that file refers to your first hard disk. (Unless you explicitly create a duplicate device file or symbolic link.)

---

### Post by jaycee23 on 2010-05-05
Thanks srs - that did the trick and thanks for the explanation. Still haven't got grub menu as I would like but will have to come back to that when I get some more time

---

### Post by jaycee23 on 2010-05-06
Now set up with lucid's grub on sda with Win 7 and karmic on sda and lucid on sdb.

When I input ```
sudo cat /boot/grub/grub.cfg | grep "menuentry" | cut -d '"' -f 2
```to preview my grub menu it looks like this

```
menuentry 'Lucid, with Linux 2.6.32-22' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Lucid, with Linux 2.6.32-22 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Lucid, with Linux 2.6.32-21' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Lucid, with Linux 2.6.32-21 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
Windows 7 (loader) (on /dev/sda1)
Karmic 2.6.31-21 (on /dev/sda7)
```I've used the tweaks on this website

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

but still the entries for Lucid look cumbersome and clumsy. The output of
```
gksu gedit /etc/grub.d/10_linux
```looks like this

```
prefix=/usr
exec_prefix=${prefix}
bindir=${exec_prefix}/bin
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

export TEXTDOMAIN=grub
export TEXTDOMAINDIR=@LOCALEDIR@

CLASS="--class gnu-linux --class gnu --class os"

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr '[A-Z]' '[a-z]' | cut -d' ' -f1) ${CLASS}"
fi

# loop-AES arranges things so that /dev/loop/X can be our root device, but
# the initrds that Linux uses don't like that.
case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
    # We can't cope with devices loop-mounted from files here.
    case ${GRUB_DEVICE} in
      /dev/*) ;;
      *) exit 0 ;;
    esac
  ;;
esac

if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
    || [ "`grub-probe -t abstraction --device ${GRUB_DEVICE} | sed -e 's,.*\(lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
else
  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"
  if ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
    recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
      cat << EOF
    set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(printf "$(gettext_quoted "Loading Linux %s ...")" ${version})'
EOF
  fi
  cat << EOF
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
    echo    '$(gettext_quoted "Loading initial ramdisk ...")'
EOF
  fi
  if test -n "${initrd}" ; then
    cat << EOF
    initrd    ${rel_dirname}/${initrd}
EOF
  fi
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`
prepare_boot_cache=

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
# User-added variable
  codename="`lsb_release -cs | sed "s/^./\u&/"`"
  version_no_generic="`echo ${version} | cut -d "-" -f 1-2`"
  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
       "initrd-${version}" "initrd.img-${alt_version}" \
       "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
    linux_root_device_thisversion=${GRUB_DEVICE}
  fi

  linux_entry "${codename}" "${version_no_generic}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${codename}" "${version_no_generic}" true \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```Sorry for the lengthy post but hopefully it contains any info you may need to helkp.
Any help much appreciated

---

