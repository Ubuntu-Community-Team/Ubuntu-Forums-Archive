---
title: "VLC / SMB - Watching videos via network-computer"
date: 2021-02-10
forum: Networking &amp; Wireless
---

### Post by Asif_Ahmad on 2021-02-10
Hey Everyone,


I am having problems watching videos over a network-connection using VLC and MPV media players. I have Ubuntu Gnome (20.04) installed on my laptop and I am trying to access my Mac Mini server (Running MacOS Big Sur) over SMB Protocol to watch videos / movies (streaming) on VLC. When I try to open a video on a network-share via smb / VLC, I get the following error message:

**VLC is unable to open the MRL &#8216;smb://pc_name/directory/Scrubs%20-%20S03E02.avi&#8217;**

What I am trying to understand:


[LIST]
[*]Is a problem with the smb password / authentication (also i don&#8217;t think so) - I have set my SMB password inside VLC preferences with no improvements.
[/LIST]

[LIST]
[*]All my other devices (Apple Laptops, Windows Laptops, Phones, etc.) can access the Mac Mini server and play videos without ANY issues.
[/LIST]

[LIST]
[*]When I copy the file (also over SMB) locally to my laptop, I can then play the video in VLC with NO issues.
[/LIST]

When I try to play things in the command line, using MPV, this is the output I get:

````
mpv -v '/run/user/1000/gvfs/smb-share:server=asifs-mac-mini.local,share=asifs%20hd/Asif/Bolt.avi'                                                             &#57522; 2 &#10008; 
[cplayer] Command line options: '-v' '/run/user/1000/gvfs/smb-share:server=asifs-mac-mini.local,share=asifs%20hd/Asif/Bolt.avi'
[cplayer] mpv 0.33.0 Copyright © 2000-2020 mpv/MPlayer/mplayer2 projects
[cplayer]  built on UNKNOWN
[cplayer] FFmpeg library versions:
[cplayer]    libavutil       56.51.100
[cplayer]    libavcodec      58.91.100
[cplayer]    libavformat     58.45.100
[cplayer]    libswscale      5.7.100
[cplayer]    libavfilter     7.85.100
[cplayer]    libswresample   3.7.100
[cplayer] FFmpeg version: n4.3.1
[cplayer] 
[cplayer] Configuration: /usr/bin/waf configure --prefix=/usr --confdir=/etc/mpv --enable-cdda --enable-dvb --enable-dvdnav --enable-libarchive --enable-libmpv-shared --disable-build-date
[cplayer] List of enabled features: 52arch alsa asm caca cdda cplayer cplugins cuda-hwaccel cuda-interop debug-build drm dvbin dvdnav egl egl-drm egl-helpers egl-x11 ffmpeg ffnvcodec gbm gbm.h gl gl-wayland glibc-thread-name glob glob-posix gpl iconv jack javascript jpeg lcms2 libarchive libass libavdevice libbluray libdl libm libmpv-shared libplacebo librt linux-fstatfs linux-input-event-codes lua memfd_create optimize plain-gl posix posix-or-mingw pthreads pulse rubberband shaderc shaderc-shared stdatomic uchardet vaapi vaapi-drm vaapi-egl vaapi-vulkan vaapi-wayland vaapi-x-egl vaapi-x11 vdpau vt.h vulkan wayland wayland-protocols x11 xv zlib
[cplayer] Reading config file /etc/mpv/encoding-profiles.conf
[cplayer] Applying profile 'default'...
[cplayer] Setting option 'v' = '' (flags = 8)
[cplayer] Waiting for scripts...
[osd/libass] Shaper: FriBidi 1.0.10 (SIMPLE) HarfBuzz-ng 2.7.4 (COMPLEX)
[osd/libass] Setting up fonts...
[osd/libass] Using font provider fontconfig
[osd/libass] Done.
[cplayer] Set property: shared-script-properties -> 1
[cplayer] Done loading scripts.
[cplayer] Running hook: ytdl_hook/on_load
[ytdl_hook] ytdl:// hook 
[ytdl_hook] not a ytdl:// url 
[ifo_dvdnav] Opening /run/user/1000/gvfs/smb-share:server=asifs-mac-mini.local,share=asifs%20hd/Asif/Bolt.avi
[cplayer] Set property: shared-script-properties -> 1
[osd/libass] Shaper: FriBidi 1.0.10 (SIMPLE) HarfBuzz-ng 2.7.4 (COMPLEX)
[osd/libass] Setting up fonts...
[osd/libass] Using font provider fontconfig
[osd/libass] Done.
[cplayer] Set property: shared-script-properties -> 1
[bdmv/bluray] Opening /run/user/1000/gvfs/smb-share:server=asifs-mac-mini.local,share=asifs%20hd/Asif/Bolt.avi
[file] Opening /run/user/1000/gvfs/smb-share:server=asifs-mac-mini.local,share=asifs%20hd/Asif/Bolt.avi
[demux] Trying demuxers for level=normal.
[lavf] No format found, try lowering probescore or forcing the format.
[demux] Trying demuxers for level=unsafe.
[lavf] No format found, try lowering probescore or forcing the format.
[cplayer] Opening failed or was aborted: /run/user/1000/gvfs/smb-share:server=asifs-mac-mini.local,share=asifs%20hd/Asif/Bolt.avi
[cplayer] Running hook: ytdl_hook/on_load_fail
[ytdl_hook] full hook 
[cplayer] finished playback, unrecognized file format (reason 4)
[cplayer] Failed to recognize file format.
[cplayer] 
[cplayer] Exiting... (Errors when loading file)
[cplayer] Set property: shared-script-properties -> 1
````

So this makes me think it is a SMB / connection issue to the Mac Mini Server, and ONLY with Ubuntu, and no other devices, since I am able to copy and then play the files locally. If anyone has any ideas / feedback / advice, it would be greatly appreciated. 

Thanks for any help you can provide!

---

### Post by TheFu on 2021-02-11
Check the version of SMB protocol supported by the Mac. 
Also, consider using a real mount - via the fstab using the CIFS method.

---

### Post by bpmildh on 2021-02-28
I have the same situation with Ubuntu 20.10 as client and MacOS Big sur as file server. The suggestion from TheFu to use fstab och cifs put me on the right path, but it took a lot of googling to get it right.
There are literally thousands ways of doing this. My solution make the connection work similar to how it works in a Mac-to-Mac situation, without all the linux server voodoo you might not need in a home environment.

1. Create a new folder in /home/yourusername/mnt/ . Don't use sudo, Nautilus is good enough. If you name the folder "share" the path will be /home/yourusername/mnt/share
2 Create a textfile with the server login-credetials in a file named .smbcredentials in your home directory. No sudo here either. Like this:
```
username=user
password=pass
domain=WORKGROUP
```
3. Put a line similar to this in the bottom of the file fstab in /etc ( /etc/fstab ). Now you need to use sudo.
```
//your-server-name.local/shared-folder-on-mac   /home/yourusername/mnt/share   cifs    noauto,user,credentials=/home/yourusername/.smbcredentials   0    0
```
I use the options "noauto" for manual mount and "user" to be able to make changes in the shared folder.

Done. Now you should see an icon for "share" in the sidebar of Nautilus that you simply just click to mount and unmount.

You can run cifs in terminal to test the connection and try out other configurations, before you edit the fstab file. Like this:
```
sudo mount -t cifs -o username=yourusername,password=yourpassword,domain=WORKGROUP //your-server-name.local/shared-folder-on-mac /mnt/share
```
You need to use sudo here before the server is set up in fstab and you also need to create the share-folder in /mnt/ with sudo and mkdir in terminal.

More linux-savvy people are welcome to correct me :)

---

### Post by TheFu on 2021-02-28
All good, except I'd strongly recommend AGAINST mounting storage under a HOME directory.  Use somewhere else and in your HOME, use a symlink to that other storage to make access convenient.

Let's take this config line apart a little.
```
//your-server-name.local/shared-folder-on-mac   /home/yourusername/mnt/share   cifs    noauto,user,credentials=/home/yourusername/.smbcredentials   0    0
```

**your-server-name.local** assumes that ZeroConf is running on the client and server. That isn't always the situation, so it may not work. Nerds would have an internal LAN DNS running and have your-server-name setup with a static IP address.  Servers or desktops providing services should always have a static IP. Worst case, the IP address can be used. To test stuff, 
```
$ ping your-server-name.local
```
If that works, you should be fine.

**/home/yourusername/mnt/share** assumes someone created the directories. The command to do that is:
```
mkdir -p /home/yourusername/mnt/share
```
Adding more storage under a HOME will create a mixed file system environment for your backup tool. Also, since mounted storage usually is much larger, when backups do run, it is likely they will fill up.  Say you mount the storage some where else, NOT in the HOME, perhaps /media/myMac.  Then you create a symbolic link 
```
cd ~
ln -s /media/myMac
```
Now you can access that storage as ~/myMac/ using any programs you like. It is still convenient. Your backups will get the symlink, but shouldn't *follow it* unless the settings for the backup are set to "*follow symlinks*" or something like that.

```
credentials=/home/yourusername/.smbcredentials
``` is close to what you want.  But the file permissions need to specifically be set to only allow your userid any access.  Let's lock those down some:
```
chmod 600 ~/.smbcredentials
```
I probably wouldn't place the credentials file in my HOME - a little obscurity won't hurt, but the location isn't THAT important.  I'd put it in ~/bin/, but that's because I put all my scripts there and I'm positive I will never forget to include that location in my backups.  In reality, I put credential files in */root/smb/{hostname}-{drive}.creds*. This means different systems and different shared storage can be CIFS mounts. The filename clearly shows that is used for which. I can leave off the {drive} part if the credentials to access all the shares on a system are the same. Flexible and descriptive.  In reality, I use autofs to mount storage on-demand and u-mount it when it isn't used any more. This is a new can of worms, probably not worth the effort for most people, but it is handy for all temporary and network storage mounts that can disappear.

The rest of the cifs fstab line is fine. I use a few more options like the file_mode, dir_mode, and iocharset=utf8 to force some things. If you don't care, I wouldn't worry.  I don't use CIFS with Unix systems.  Unix is native NFS land.  I'd use NFS for sharing between OSX and Linux and any other Unix.  Samba is only for use with Windows in my world.  Usually, NFS is faster, smoother, and provides native permissions, which is a big deal to me.  People using Kodi know that NFS storage doesn't stutter nearly as often as CIFS/Samba storage does.  In theory, it shouldn't matter, but it does.

---

