---
title: "TrueCrypt mount options?"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by bryceowen on 2010-12-16
Does anyone know where I can find a list of options TrueCrypt will accept with the --mount-options switch? I looked through the documentation on truecrypt.org, but there was nothing in there about the console only version of the software.

I'm using Lucid server and I'm trying to mount a TC volume as a folder I can access through Apache2. The mount point I created is /var/www/testing with permissions 755. I'm able to access it through a web browser (shows an empty folder) with no problem. When I mount my TC volume, however, the permissions change to 700 and I get a 'Forbidden' message when I try to access it.

I've read a few posts on the TC forums where people say you use the 'mount-options' switch, but every option I try throws an error:
Error: Unknown option: xxx
Someone please help!

---

### Post by bryceowen on 2010-12-16
Well, I finally found a workaround. If I umount /var/www/testing and remount it using:
```
sudo mount -t vfat -o rw,uid=1000,gid=1000,umask=022 /dev/mapper/truecrypt1 /var/www/testing
```
I'm able to access the folder through a web browser. Now, if only I could get TC to set the umask directly rather than me having to unmount and remount the folder...

---

### Post by pintcat on 2011-01-01
Same here. I studied the documentary, but it doesn't say a word about these mount options. The only option I figured out till now is "nls=utf8" which is apparently necessary to mount NTFS volumes correctly. Is there a reference to these options?

---

### Post by rsk02 on 2011-01-02
I am trying to find a generic solution to mounting volumes thru fstab. In my searches, I found this: [http://en.gentoo-wiki.com/wiki/TrueCrypt](http://en.gentoo-wiki.com/wiki/TrueCrypt). You might find it useful although I could not really get that helper function to work. Also, here is what I get from the help file for the GUI version for linux:

Synopsis:

truecrypt [OPTIONS] COMMAND
truecrypt [OPTIONS] VOLUME_PATH [MOUNT_DIRECTORY]


Commands:

--auto-mount=devices|favorites
 Auto mount device-hosted or favorite volumes.

--backup-headers[=VOLUME_PATH]
 Backup volume headers to a file. All required options are requested from the
 user.

-c, --create[=VOLUME_PATH]
 Create a new volume. Most options are requested from the user if not specified
 on command line. See also options --encryption, -k, --filesystem, --hash, -p,
 --random-source, --quick, --size, --volume-type. Note that passing some of the
 options may affect security of the volume (see option -p for more information).

 Inexperienced users should use the graphical user interface to create a hidden
 volume. When using the text user interface, the following procedure must be
 followed to create a hidden volume:
  1) Create an outer volume with no filesystem.
  2) Create a hidden volume within the outer volume.
  3) Mount the outer volume using hidden volume protection.
  4) Create a filesystem on the virtual device of the outer volume.
  5) Mount the new filesystem and fill it with data.
  6) Dismount the outer volume.
  If at any step the hidden volume protection is triggered, start again from 1).

--create-keyfile[=FILE_PATH]
 Create a new keyfile containing pseudo-random data.

-C, --change[=VOLUME_PATH]
 Change a password and/or keyfile(s) of a volume. Most options are requested
 from the user if not specified on command line. PKCS-5 PRF HMAC hash
 algorithm can be changed with option --hash. See also options -k,
 --new-keyfiles, --new-password, -p, --random-source.

-d, --dismount[=MOUNTED_VOLUME]
 Dismount a mounted volume. If MOUNTED_VOLUME is not specified, all
 volumes are dismounted. See below for description of MOUNTED_VOLUME.

--delete-token-keyfiles
 Delete keyfiles from security tokens. See also command --list-token-keyfiles.

--export-token-keyfile
 Export a keyfile from a security token. See also command --list-token-keyfiles.

--import-token-keyfiles
 Import keyfiles to a security token. See also option --token-lib.

-l, --list[=MOUNTED_VOLUME]
 Display a list of mounted volumes. If MOUNTED_VOLUME is not specified, all
 volumes are listed. By default, the list contains only volume path, virtual
 device, and mount point. A more detailed list can be enabled by verbose
 output option (-v). See below for description of MOUNTED_VOLUME.

--list-token-keyfiles
 Display a list of all available security token keyfiles. See also command
 --import-token-keyfiles.

--mount[=VOLUME_PATH]
 Mount a volume. Volume path and other options are requested from the user
 if not specified on command line.

--restore-headers[=VOLUME_PATH]
 Restore volume headers from the embedded or an external backup. All required
 options are requested from the user.

--save-preferences
 Save user preferences.

--test
 Test internal algorithms used in the process of encryption and decryption.

--version
 Display program version.

--volume-properties[=MOUNTED_VOLUME]
 Display properties of a mounted volume. See below for description of
 MOUNTED_VOLUME.

MOUNTED_VOLUME:
 Specifies a mounted volume. One of the following forms can be used:
 1) Path to the encrypted TrueCrypt volume.
 2) Mount directory of the volume's filesystem (if mounted).
 3) Slot number of the mounted volume (requires --slot).


Options:

--display-password
 Display password characters while typing.

--encryption=ENCRYPTION_ALGORITHM
 Use specified encryption algorithm when creating a new volume.

--filesystem=TYPE
 Filesystem type to mount. The TYPE argument is passed to mount(8) command
 with option -t. Default type is 'auto'. When creating a new volume, this
 option specifies the filesystem to be created on the new volume (only 'FAT'
 and 'none' TYPE is allowed). Filesystem type 'none' disables mounting or
 creating a filesystem.

--force
 Force mounting of a volume in use, dismounting of a volume in use, or
 overwriting a file. Note that this option has no effect on some platforms.

--fs-options=OPTIONS
 Filesystem mount options. The OPTIONS argument is passed to mount(8)
 command with option -o when a filesystem on a TrueCrypt volume is mounted.
 This option is not available on some platforms.

--hash=HASH
 Use specified hash algorithm when creating a new volume or changing password
 and/or keyfiles. This option also specifies the mixing PRF of the random
 number generator.

-k, --keyfiles=KEYFILE1[,KEYFILE2,KEYFILE3,...]
 Use specified keyfiles when mounting a volume or when changing password
 and/or keyfiles. When a directory is specified, all files inside it will be
 used (non-recursively). Multiple keyfiles must be separated by comma.
 Use double comma (,,) to specify a comma contained in keyfile's name.
 Keyfile stored on a security token must be specified as
 token://slot/SLOT_NUMBER/file/FILENAME. An empty keyfile (-k "") disables
 interactive requests for keyfiles. See also options --import-token-keyfiles,
 --list-token-keyfiles, --new-keyfiles, --protection-keyfiles.

--load-preferences
 Load user preferences.

-m, --mount-options=OPTION1[,OPTION2,OPTION3,...]
 Specifies comma-separated mount options for a TrueCrypt volume:
  headerbak: Use backup headers when mounting a volume.
  nokernelcrypto: Do not use kernel cryptographic services.
  readonly|ro: Mount volume as read-only.
  system: Mount partition using system encryption.
  timestamp|ts: Do not restore host-file modification timestamp when a volume
   is dismounted (note that the operating system under certain circumstances
   does not alter host-file timestamps, which may be mistakenly interpreted
   to mean that this option does not work).
 See also option --fs-options.

--new-keyfiles=KEYFILE1[,KEYFILE2,KEYFILE3,...]
 Add specified keyfiles to a volume. This option can only be used with command
 -C.

--new-password=PASSWORD
 Specifies a new password. This option can only be used with command -C.

-p, --password=PASSWORD
 Use specified password to mount/open a volume. An empty password can also be
 specified (-p ""). Note that passing a password on the command line is
 potentially insecure as the password may be visible in the process list
 (see ps(1)) and/or stored in a command history file or system logs.

--protect-hidden=yes|no
 Write-protect a hidden volume when mounting an outer volume. Before mounting
 the outer volume, the user will be prompted for a password to open the hidden
 volume. The size and position of the hidden volume is then determined and the
 outer volume is mounted with all sectors belonging to the hidden volume
 protected against write operations. When a write to the protected area is
 prevented, the whole volume is switched to read-only mode. Verbose list
 (-v -l) can be used to query the state of the hidden volume protection.
 Warning message is displayed when a volume switched to read-only is being
 dismounted.

--protection-keyfiles=KEYFILE1[,KEYFILE2,KEYFILE3,...]
 Use specified keyfiles to open a hidden volume to be protected. This option
 may be used only when mounting an outer volume with hidden volume protected.
 See also options -k and --protect-hidden.

--protection-password=PASSWORD
 Use specified password to open a hidden volume to be protected. This option
 may be used only when mounting an outer volume with hidden volume protected.
 See also options -p and --protect-hidden.

--quick
 Do not encrypt free space when creating a device-hosted volume. This option
 must not be used when creating an outer volume.

--random-source=FILE
 Use FILE as a source of random data (e.g., when creating a volume) instead
 of requiring the user to type random characters.

--slot=SLOT
 Use specified slot number when mounting, dismounting, or listing a volume.

--size=SIZE
 Use specified size in bytes when creating a new volume.

-t, --text
 Use text user interface. Graphical user interface is used by default if
 available. This option must be specified as the first argument.

--token-lib=LIB_PATH
 Use specified PKCS #11 security token library.

--volume-type=TYPE
 Use specified volume type when creating a new volume. TYPE can be 'normal'
 or 'hidden'. See option -c for more information on creating hidden volumes.

-v, --verbose
 Enable verbose output.


IMPORTANT:

If you want to use TrueCrypt, you must follow the security requirements and
security precautions listed in chapter 'Security Requirements and Precautions'
in the TrueCrypt documentation (file 'TrueCrypt User Guide.pdf').


Examples:

Create a new volume:
truecrypt -t -c

Mount a volume:
truecrypt volume.tc /media/truecrypt1

Mount a volume as read-only, using keyfiles:
truecrypt -m ro -k keyfile1,keyfile2 volume.tc

Mount a volume without mounting its filesystem:
truecrypt --filesystem=none volume.tc

Mount a volume prompting only for its password:
truecrypt -t -k "" --protect-hidden=no volume.tc /media/truecrypt1

Dismount a volume:
truecrypt -d volume.tc

Dismount all mounted volumes:
truecrypt -d

---

