---
title: "Wireless driver help"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-02-03
Hello recently installed ubuntu 8.10, pretty cool and all but i cant get it wireless.

I went onto my hardware drivers and support for Atheros 802-11 wireless lan cards was active.

Dosent this mean i should be able to go wireless.

I have also put in my Ip subnet gateway  and when i click ok it asks for my password, i put it in and nothing happends.

I have also put in Iwconfig in the terminal and it gave me.

Lo- no wireless extensions
etho- no wireless extensions
pano- no wireless extensions

Help please

---

### Post by kestrel1 on 2009-02-03
You need to first determine if your wireless card is supported underUbuntu. To do this go [HERE]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
You will need to type ```
lspci -v | less
```
If you could also post the output it may be useful.

---

### Post by sp0nge on 2009-02-03
[This link]("http://linuxwireless.org/en/users/Download") will take you to the site I used to set mine up, this seems to encompass most of the ath chipset.

---

### Post by Rave Gloves on 2009-02-03
> **kestrel1 said:**
> You need to first determine if your wireless card is supported underUbuntu. To do this go [HERE]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
You will need to type ```
lspci -v | less
```
If you could also post the output it may be useful.

00:00.0 Host bridge: intel corporation mobile 4 series chipset memory controller
Subsystem: Samsung corperation 
<access denied
Kernel Modual: intel-cpy

00:01.0 PCI bridge: intel corperation mobile 4 series chipset PCI express graphics port (rev 07)
Access denied
Kernel driver in use: pcieport-driver
kernel moduals: shpchp

00:1a.0 intel corp 8280.11 (Ich9 family) lesb uhci controller 4 rev 03

I/o ports at 1800



Some of these may be wrong and i have missed out parts that i thought wouldnt be important, its pretty hard copying it all down on paper then copying it over to here.

---

### Post by Rave Gloves on 2009-02-03
> **sp0nge said:**
> [This link]("http://linuxwireless.org/en/users/Download") will take you to the site I used to set mine up, this seems to encompass most of the ath chipset.

Cheers for the link but dont i need internet to download drivers?

---

### Post by mattman85 on 2009-02-03
> **sp0nge said:**
> [This link]("http://linuxwireless.org/en/users/Download") will take you to the site I used to set mine up, this seems to encompass most of the ath chipset.

that site is definitely a good place to start..

---

### Post by mattman85 on 2009-02-03
> **Rave Gloves said:**
> Cheers for the link but dont i need internet to download drivers?

yes, but you can write down your hardware specs (name, etc, of the wireless card) and then go to wherever you're accessing UbuntuForums from, and find it that way ;-)  save the files to USB, and then take them with you.

---

### Post by kestrel1 on 2009-02-03
You should be able to select what you want to post & copy & paste it.
You can always leave the | less part of the command off & this will list everything without stopping & you just need to scroll up the list.
Use you mouse to select, right click on the selection & chose copy, then in the thread's message box use Paste, from a right click again.

---

### Post by Rave Gloves on 2009-02-03
> **kestrel1 said:**
> You should be able to select what you want to post & copy & paste it.
You can always leave the | less part of the command off & this will list everything without stopping & you just need to scroll up the list.
Use you mouse to select, right click on the selection & chose copy, then in the thread's message box use Paste, from a right click again.

Yes but i have a duo boot with vista so when i need the internet i swtich over to vista and use it there, i know you can copy paste the output but i cant do that when i need to restart and go to vista

---

### Post by Rave Gloves on 2009-02-03
> **mattman85 said:**
> yes, but you can write down your hardware specs (name, etc, of the wireless card) and then go to wherever you're accessing UbuntuForums from, and find it that way ;-)  save the files to USB, and then take them with you.

Ah i see, cheers i will give it a try.

---

### Post by mattman85 on 2009-02-03
> **Rave Gloves said:**
> Ah i see, cheers i will give it a try.

hopefully it helps!

---

### Post by avtolle on 2009-02-03
If you are going to the site linked, download the driver and transport it back to your Ubuntu box. Then, follow the directions given on the site to compile the file (which contains a large number of drivers, including the ath5k and ath9k ones) and install it. FWIW, this resolved my problem with an Atheros card on 64-bit 8.10 quite nicely.

EDIT: Meant to say, download the tarball, not the driver. Installation, once the file is extracted and the commands are run, is easy, and, as related earlier, resolved my problems with the Atheros card in a very satisfactory manner.

---

### Post by kestrel1 on 2009-02-03
One suggestion on copy & switching to Vista. Paste what you want in to a text document & save it on your Vista partition. That way you could paste the output in the forum.

---

### Post by Rave Gloves on 2009-02-03
is there any reason that

You can compat-wireless for kernels >= 2.6.27 here:

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

isnt working?

Is the link broken?

---

### Post by yipster on 2009-02-03
all i needed to do was ask internet provider (talktalk HAHA)what settings I needed in my router and they told me .... no need for them to know i'm on linux

---

### Post by Rave Gloves on 2009-02-04
Hey i need some more help.

where it says ```
cd compat-wireless-$(date -I)
make
```

Where it says (date -I) do i put the date on the tarball?

---

### Post by Rave Gloves on 2009-02-04
Come on can someone help me?

I have no idea what im doing i have the tarbell file over to my ubuntu system but all the codes it tell me to put in are giving me errors and im really confused.

HELP

---

### Post by kestrel1 on 2009-02-04
What errors are you getting?

---

### Post by stchman on 2009-02-04
> **Rave Gloves said:**
> Come on can someone help me?

I have no idea what im doing i have the tarbell file over to my ubuntu system but all the codes it tell me to put in are giving me errors and im really confused.

HELP

Post an lspci terminal output in this thread.  We need the exact model of Atheros card you have.  To get an lspci output open a terminal and type:

```
lspci
```

and post the output here in this thread.

---

### Post by Rave Gloves on 2009-02-04
The errors im getting is:

tar compat-wireless-2009-02-04.tar.bz2:cannot open: no such file in directory
tar:error is not recoverable exiting now
tar: child returned status 2
tar: error exit delayed from previous errors


I will get the other out put in 2mins

---

### Post by kestrel1 on 2009-02-04
This error is telling you that the directory you are currently in does not contain the file you are trying to run tar with.
You need to cd to the files location.
If it is saved to your desktop first type:```
cd Desktop
```
Then run:```
tar compat-wireless-2009-02-04.tar.bz2
```
Obviously if the file is in a diferent location cd to that directory. To check that the file is there & you are spelling it correctly type:```
ls
``` when you have entered the directory.

---

### Post by Rave Gloves on 2009-02-04
^
Cheers i shall try it.

here is what i got when i put in lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)

---

### Post by Rave Gloves on 2009-02-04
> **kestrel1 said:**
> This error is telling you that the directory you are currently in does not contain the file you are trying to run tar with.
You need to cd to the files location.
If it is saved to your desktop first type:```
cd Desktop
```
Then run:```
tar compat-wireless-2009-02-04.tar.bz2
```
Obviously if the file is in a diferent location cd to that directory. To check that the file is there & you are spelling it correctly type:```
ls
``` when you have entered the directory.

Well i done what you said and this happend i typed in the code for help that it gave me.

andrew@andrew-laptop:~$ cd Desktop
andrew@andrew-laptop:~/Desktop$ tar compat-wireless-2009-02-04.tat.bz2
tar: Old option `b' requires an argument.
Try `tar --help' or `tar --usage' for more information.
andrew@andrew-laptop:~/Desktop$ tar --help
Usage: tar [OPTION...] [FILE]...
GNU `tar' saves many files together into a single tape or disk archive, and can
restore individual files from the archive.

Examples:
  tar -cf archive.tar foo bar  # Create archive.tar from files foo and bar.
  tar -tvf archive.tar         # List all files in archive.tar verbosely.
  tar -xf archive.tar          # Extract all files from archive.tar.

 Main operation mode:

  -A, --catenate, --concatenate   append tar files to an archive
  -c, --create               create a new archive
  -d, --diff, --compare      find differences between archive and file system
      --delete               delete from the archive (not on mag tapes!)
  -r, --append               append files to the end of an archive
  -t, --list                 list the contents of an archive
      --test-label           test the archive volume label and exit
  -u, --update               only append files newer than copy in archive
  -x, --extract, --get       extract files from an archive

 Operation modifiers:

      --check-device         check device numbers when creating incremental
                             archives (default)
  -g, --listed-incremental=FILE   handle new GNU-format incremental backup
  -G, --incremental          handle old GNU-format incremental backup
      --ignore-failed-read   do not exit with nonzero on unreadable files
  -n, --seek                 archive is seekable
      --no-check-device      do not check device numbers when creating
                             incremental archives
      --occurrence[=NUMBER]  process only the NUMBERth occurrence of each file
                             in the archive; this option is valid only in
                             conjunction with one of the subcommands --delete,
                             --diff, --extract or --list and when a list of
                             files is given either on the command line or via
                             the -T option; NUMBER defaults to 1
      --sparse-version=MAJOR[.MINOR]
                             set version of the sparse format to use (implies
                             --sparse)
  -S, --sparse               handle sparse files efficiently

 Overwrite control:

  -k, --keep-old-files       don't replace existing files when extracting
      --keep-newer-files     don't replace existing files that are newer than
                             their archive copies
      --no-overwrite-dir     preserve metadata of existing directories
      --overwrite            overwrite existing files when extracting
      --overwrite-dir        overwrite metadata of existing directories when
                             extracting (default)
      --recursive-unlink     empty hierarchies prior to extracting directory
      --remove-files         remove files after adding them to the archive
  -U, --unlink-first         remove each file prior to extracting over it
  -W, --verify               attempt to verify the archive after writing it

 Select output stream:

      --ignore-command-error ignore exit codes of children
      --no-ignore-command-error   treat non-zero exit codes of children as
                             error
  -O, --to-stdout            extract files to standard output
      --to-command=COMMAND   pipe extracted files to another program

 Handling of file attributes:

      --atime-preserve[=METHOD]   preserve access times on dumped files, either
                             by restoring the times after reading
                             (METHOD='replace'; default) or by not setting the
                             times in the first place (METHOD='system')
      --delay-directory-restore   delay setting modification times and
                             permissions of extracted directories until the end
                             of extraction
      --group=NAME           force NAME as group for added files
      --mode=CHANGES         force (symbolic) mode CHANGES for added files
      --mtime=DATE-OR-FILE   set mtime for added files from DATE-OR-FILE
  -m, --touch                don't extract file modified time
      --no-delay-directory-restore
                             cancel the effect of --delay-directory-restore
                             option
      --no-same-owner        extract files as yourself
      --no-same-permissions  apply the user's umask when extracting permissions
                             from the archive (default for ordinary users)
      --numeric-owner        always use numbers for user/group names
      --owner=NAME           force NAME as owner for added files
  -p, --preserve-permissions, --same-permissions
                             extract information about file permissions
                             (default for superuser)
      --preserve             same as both -p and -s
      --same-owner           try extracting files with the same ownership
  -s, --preserve-order, --same-order
                             sort names to extract to match archive

 Device selection and switching:

  -f, --file=ARCHIVE         use archive file or device ARCHIVE
      --force-local          archive file is local even if it has a colon
  -F, --info-script=NAME, --new-volume-script=NAME
                             run script at end of each tape (implies -M)
  -L, --tape-length=NUMBER   change tape after writing NUMBER x 1024 bytes
  -M, --multi-volume         create/list/extract multi-volume archive
      --rmt-command=COMMAND  use given rmt COMMAND instead of rmt
      --rsh-command=COMMAND  use remote COMMAND instead of rsh
      --volno-file=FILE      use/update the volume number in FILE

 Device blocking:

  -b, --blocking-factor=BLOCKS   BLOCKS x 512 bytes per record
  -B, --read-full-records    reblock as we read (for 4.2BSD pipes)
  -i, --ignore-zeros         ignore zeroed blocks in archive (means EOF)
      --record-size=NUMBER   NUMBER of bytes per record, multiple of 512

 Archive format selection:

  -H, --format=FORMAT        create archive of the given format

 FORMAT is one of the following:

    gnu                      GNU tar 1.13.x format
    oldgnu                   GNU format as per tar <= 1.12
    pax                      POSIX 1003.1-2001 (pax) format
    posix                    same as pax
    ustar                    POSIX 1003.1-1988 (ustar) format
    v7                       old V7 tar format

      --old-archive, --portability
                             same as --format=v7
      --pax-option=keyword[[:]=value][,keyword[[:]=value]]...
                             control pax keywords
      --posix                same as --format=posix
  -V, --label=TEXT           create archive with volume name TEXT; at
                             list/extract time, use TEXT as a globbing pattern
                             for volume name

 Compression options:

  -a, --auto-compress        use archive suffix to determine the compression
                             program
  -j, --bzip2                filter the archive through bzip2
      --lzma                 filter the archive through lzma
      --use-compress-program=PROG
                             filter through PROG (must accept -d)
  -z, --gzip, --gunzip, --ungzip   filter the archive through gzip
  -Z, --compress, --uncompress   filter the archive through compress

 Local file selection:

      --add-file=FILE        add given FILE to the archive (useful if its name
                             starts with a dash)
      --backup[=CONTROL]     backup before removal, choose version CONTROL
  -C, --directory=DIR        change to directory DIR
      --exclude=PATTERN      exclude files, given as a PATTERN
      --exclude-caches       exclude contents of directories containing
                             CACHEDIR.TAG, except for the tag file itself
      --exclude-caches-all   exclude directories containing CACHEDIR.TAG
      --exclude-caches-under exclude everything under directories containing
                             CACHEDIR.TAG
      --exclude-tag=FILE     exclude contents of directories containing FILE,
                             except for FILE itself
      --exclude-tag-all=FILE exclude directories containing FILE
      --exclude-tag-under=FILE   exclude everything under directories
                             containing FILE
      --exclude-vcs          exclude version control system directories
  -h, --dereference          follow symlinks; archive and dump the files they
                             point to
      --hard-dereference     follow hard links; archive and dump the files they
                             refer to
  -K, --starting-file=MEMBER-NAME
                             begin at member MEMBER-NAME in the archive
      --newer-mtime=DATE     compare date and time when data changed only
      --no-recursion         avoid descending automatically in directories
      --no-unquote           do not unquote filenames read with -T
      --null                 -T reads null-terminated names, disable -C
  -N, --newer=DATE-OR-FILE, --after-date=DATE-OR-FILE
                             only store files newer than DATE-OR-FILE
      --one-file-system      stay in local file system when creating archive
  -P, --absolute-names       don't strip leading `/'s from file names
      --recursion            recurse into directories (default)
      --suffix=STRING        backup before removal, override usual suffix ('~'
                             unless overridden by environment variable
                             SIMPLE_BACKUP_SUFFIX)
  -T, --files-from=FILE      get names to extract or create from FILE
      --unquote              unquote filenames read with -T (default)
  -X, --exclude-from=FILE    exclude patterns listed in FILE

 File name transformations:

      --strip-components=NUMBER   strip NUMBER leading components from file
                             names on extraction
      --transform=EXPRESSION use sed replace EXPRESSION to transform file
                             names

 File name matching options (affect both exclude and include patterns):

      --anchored             patterns match file name start
      --ignore-case          ignore case
      --no-anchored          patterns match after any `/' (default for
                             exclusion)
      --no-ignore-case       case-sensitive matching (default)
      --no-wildcards         verbatim string matching
      --no-wildcards-match-slash   wildcards do not match `/'
      --wildcards            use wildcards (default for exclusion)
      --wildcards-match-slash   wildcards match `/' (default for exclusion)

 Informative output:

      --checkpoint[=NUMBER]  display progress messages every NUMBERth record
                             (default 10)
      --checkpoint-action=ACTION   execute ACTION on each checkpoint
      --index-file=FILE      send verbose output to FILE
  -l, --check-links          print a message if not all links are dumped
      --no-quote-chars=STRING   disable quoting for characters from STRING
      --quote-chars=STRING   additionally quote characters from STRING
      --quoting-style=STYLE  set name quoting style; see below for valid STYLE
                             values
  -R, --block-number         show block number within archive with each
                             message
      --show-defaults        show tar defaults
      --show-omitted-dirs    when listing or extracting, list each directory
                             that does not match search criteria
      --show-transformed-names, --show-stored-names
                             show file or archive names after transformation
      --totals[=SIGNAL]      print total bytes after processing the archive;
                             with an argument - print total bytes when this
                             SIGNAL is delivered; Allowed signals are: SIGHUP,
                             SIGQUIT, SIGINT, SIGUSR1 and SIGUSR2; the names
                             without SIG prefix are also accepted
      --utc                  print file modification dates in UTC
  -v, --verbose              verbosely list files processed
  -w, --interactive, --confirmation
                             ask for confirmation for every action

 Compatibility options:

  -o                         when creating, same as --old-archive; when
                             extracting, same as --no-same-owner

 Other options:

  -?, --help                 give this help list
      --restrict             disable use of some potentially harmful options
      --usage                give a short usage message
      --version              print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control may be set with --backup or VERSION_CONTROL, values are:

  none, off       never make backups
  t, numbered     make numbered backups
  nil, existing   numbered if numbered backups exist, simple otherwise
  never, simple   always make simple backups

Valid arguments for --quoting-style options are:

  literal
  shell
  shell-always
  c
  c-maybe
  escape
  locale
  clocale

*This* tar defaults to:
--format=gnu -f- -b20 --quoting-style=escape --rmt-command=/usr/sbin/rmt
--rsh-command=/usr/bin/rsh

Report bugs to <bug-tar@gnu.org>.
andrew@andrew-laptop:~/Desktop$

---

### Post by nothingspecial on 2009-02-04
Go to system > administration > hardware drivers then disable anything in there.

Then

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver

```
sudo modprobe ath5k
```

To make it load everytime you boot```


gksudo gedit /etc/modules
```

and add

```
ath5k
```

To the end of the file

save
close
reboot

---

### Post by Rave Gloves on 2009-02-04
Wont i need an internet connection to do this?

---

### Post by nothingspecial on 2009-02-04
Yep.

If you can`t get a wired one but have a connection on another computer there is a different way we can go.

---

### Post by Rave Gloves on 2009-02-04
Could you tell me how to get it offline please?

---

### Post by nothingspecial on 2009-02-04
Yes, give me a few minutes, detailed instructions to follow.

---

### Post by Rave Gloves on 2009-02-04
Thanks man, i hope this works :]

---

### Post by nothingspecial on 2009-02-04
Go here and download the third from bottom file

[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

Copy it from your internet connected computer to your Ubuntu`s Desktop.

Open a terminal 

To make sure you have the tools necessary for compiling, pop in your live cd (the one you installed from). Go to System > Administration > Software Sources. Check the cd source (in the big box at the bottom).

Close. Then
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Navigate to your Desktop

```
cd Desktop
```

"unzip" your downloaded file
```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```

Enter it
```
cd madwifi-hal-0.10.5.6*/
```

Compile it
```
make
```
```
sudo make install
```

Load the driver
```
sudo modprobe ath_pci
```

Make it load at boot

```
gksudo /etc/modules
```

Add this to the end of the file

```
ath_pci
```

(If you followed my first instructions you should comment out the line you added ath5k. Just put a # in front of it. Delete it if you like but don`t delete anything else.)

As before - save
close
Reboot

---

### Post by avtolle on 2009-02-04
> **nothingspecial said:**
> Go to system > administration > hardware drivers then disable anything in there.

Then

```
sudo apt-get install linux-backports-modules-intrepid-generic
```To load the driver

```
sudo modprobe ath5k
```To make it load everytime you boot```


gksudo gedit /etc/modules
```and add

```
ath5k
```To the end of the file

save
close


reboot
That is a good answer to your question, OP, as well; I used it also to set up my Atheros card successfully. Good luck.

---

### Post by Rave Gloves on 2009-02-04
nothingspecial: i did exactly as you said lots of code and stuff was going on but when i tried ```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```  the unzip code it didnt work it gave me the same error as back a few pages, about child and stuff, so i skiped that step and when i entered ```
cd madwifi-hal-0.10.5.6*/
```

That code lots of code went and i followed the rest and saved closed rebooted and went back on, i dont think it worked though i couldnt get it wireless.

Tommorow i will try and find my ethernet cable and do the one that i need the network for.

Thanks for all your help, i will post back in this thread when i try the network one. :]

---

