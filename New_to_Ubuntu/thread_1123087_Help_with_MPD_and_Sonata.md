---
title: "Help with MPD and Sonata"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by kratos_prakhar on 2009-04-11
hi.. i am on the ibex and i've spent almost 2-3 hrs trying to get the sonata to work as my music player and i have availed no success.. 

After searching a lot of forumds and blogs.. i found this

[http://linuxowns.wordpress.com/2008/07/27/setting-up-mpd-locally/](http://linuxowns.wordpress.com/2008/07/27/setting-up-mpd-locally/)

now i've followed the guide word by word.. but the error has come wen i use mpc update

the sudo mpd --create-db command gave me the following result on my brower:

added dev d/Emosanal Attyachaar - Brass Band Version.mp3
added dev d/Nayan Tarse.mp3
added dev d/Mahi Mennu - SadVersion.mp3
added dev d/Pardesi.mp3
added dev d/Duniya.mp3
added dev d/Hikknaal.mp3
prakhar@prakhar-laptop:~$ 

which i think is an indication of my songs being successfully added on the database...

now wen i use the mpc update command this is the error it gives me:

prakhar@prakhar-laptop:~$ mpc update
MPD_HOST and/or MPD_PORT environment variables are not set
error: problems getting a response from "localhost" on port 6600 : Connection refused

also wen i open my sonata all the windows are empty... i cant see the songs the database jst hashed :(

i would be very grateful if someone could help me out wid this problem....


my /etc/mpd.conf :


# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"~/Music"
playlist_directory	"~/.mpd/playlists"
db_file			"~/.mpd/mpd.db"
log_file		"~/.mpd/mpd.log"
error_file		"~/.mpd/mpd.error"
#pid_file		"/var/run/mpd/pid"
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/var/lib/mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "prakhar"
#
# The address and port to listen on.
#
bind_to_address                 "localhost"
port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################


########################## PERMISSIONS #########################
#
# MPD can require that users specify a password before using it.
# You may specify one ore more here, along with what users who
# log in with that password are allowed to do.
#
#password                        "password@read,add,control,admin"
#
# Specifies what permissions a user who has not logged in with a
# password has.  By default, all users have full access to MPD
# if no password is specified above, or no access if one or
# more passwords are specified.
#
#default_permissions             "read,add,control,admin"
#
################################################################


########################## AUDIO OUTPUT ########################
#
# MPD supports many audio output types, as well as playing
# through multiple audio outputs at the same time.  You can
# specify one or more here.  If you don't specify any, MPD will
# automatically scan for a usable audio output.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs>
# for examples of other audio outputs.
#
# An example of an ALSA output:
#
#audio_output {
#        type                    "alsa"
#        name                    "My ALSA Device"
#        device                  "hw:0,0"     # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of an OSS output:
#
#audio_output {
#        type                    "oss"
#        name                    "My OSS Device"
#        device                  "/dev/dsp"   # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#        type                    "shout"
#        name                    "My Shout Stream"
#        host                    "localhost"
#        port                    "8000"
#        mount                   "/mpd.ogg"
#        password                "hackme"
#        quality                 "5.0"
#        bitrate                 "128"
#        format                  "44100:16:1"
#        user                    "source"                # optional
#        description             "My Stream Description" # optional
#        genre                   "jazz"                  # optional
#        public                  "no"                    # optional
#}
#
# Force all decoded audio to be converted to this format before
# being passed to the audio outputs.
#
#audio_output_format             "44100:16:2"
#
################################################################


############################# MIXER ############################
#
# MPD needs to know what mixer settings to change when you
# adjust the volume.  If you don't specify one here, MPD will
# pick one based on which ones it was compiled with support for.
#
# An example for controlling an ALSA mixer:
#
mixer_type                      "alsa"
mixer_device                    "default"
mixer_control                   "master"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#
# If you want MPD to adjust the volume of audio sent to the
# audio outputs, you can tell it to use the software mixer:
#
#mixer_type                      "software"
#
################################################################


######################### NORMALIZATION ########################
#
# Specifies the type of ReplayGain to use.  Can be "album" or
# "track".  ReplayGain will not be used if not specified.  See
# <http://www.replaygain.org> for more details.
#
#replaygain                      "album"
#
# Sets the pre-amp used for files that have ReplayGain tags.
#
#replaygain_preamp               "0"
#
# Enable on the fly volume normalization.  This will cause the
# volume of all songs played to be adjusted so that they sound
# as though they are of equal loudness.
#
#volume_normalization            "no"
#
################################################################


########################### BUFFERING ##########################
#
# The size of the buffer containing decoded audio.  You probably
# shouldn't change this.
#
#audio_buffer_size               "2048"
#
# How much of the buffer to fill before beginning to play.
#
#buffer_before_play              "0%"
#
# Similar options for the HTTP stream buffer.  If you hear
# skipping while playing HTTP streams, you may wish to increase
# these.
#
#http_buffer_size                "128"
#http_prebuffer_size             "25%"
#
################################################################


########################### HTTP PROXY #########################
#
# Specifies the HTTP proxy to use for playing HTTP streams.
#
#http_proxy_host                 "proxy.isp.com"
#http_proxy_port                 "8080"
#http_proxy_user                 "user"
#http_proxy_password             "password"
#
################################################################


############################# LIMITS ###########################
#
# These are various limits to prevent MPD from using too many
# resources.  You should only change them if they start
# restricting your usage of MPD.
#
#connection_timeout              "60"
#max_connections                 "5"
#max_playlist_length             "16384"
#max_command_list_size           "2048"
#max_output_buffer_size          "8192"
#
################################################################


###################### CHARACTER ENCODINGS #####################
#
# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
filesystem_charset              "UTF-8"
#
# The encoding that ID3v1 tags should be converted from.
#
id3v1_encoding                  "UTF-8"
#
################################################################


######################### OTHER OPTIONS ########################
#
# The metadata types MPD will recognize.
#
#metadata_to_use                  "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# Enable this if you wish to use your MPD created playlists in
# other music players.
#
#save_absolute_paths_in_playlists "no"
#
################################################################

---

### Post by tjwoosta on 2009-04-13
hmm..

well just taking a quick look and my config seems to be a bit different from what you have  (mine is with archlinux but i think all the configuration should be the same)


here is a good resource for configuring mpd

[http://wiki.archlinux.org/index.php/Mpd]("http://wiki.archlinux.org/index.php/Mpd")


```

######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).

user                            "tj"

# The address and port to listen on.
#
bind_to_address                 "127.0.0.1"
#bind_to_address                 "any"
port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################

```

---

### Post by glotz on 2009-04-13
I think the interesting part is
bind_to_address                 "127.0.0.1"

---

### Post by mcduck on 2009-04-13
Based on my experience with MPD the problem is most likely result from wrong ownership/permissions of the music and playlist directories.

Check what permissions MPD's default directories have and try to set same on your current music directory. You might also have to change the ownership, or configure MPD to run as your own user instead of "mpd" (I'm not sure about the user part, though).

Actually the way I've found to be easiest is to keep the default directories for MPD, and then just symlink my own music directory there. This way MPD pretty much works out-of-the-box while I can still keep my music where I want.

So, what I suggest is leaving the directories in mpd.conf to defaults, and then just using some thing like this to add your music directory to MPD library:
```
sudo ln -s /path/to/your/music /var/lib/mpd/music
```
(if you want to add music from multiple directories just link them into subdirectories inside /var/lib/mpd/music instead of linking directly to the directory itself)

---

