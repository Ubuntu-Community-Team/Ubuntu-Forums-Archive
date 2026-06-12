---
title: "Problems Starting Up MPD"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by cfree220 on 2009-04-02
Hi all,

I have an audio streaming server that can push music to MPD. I've been trying to get this to work for quite some time. I've so far been able to fix the configuration of the server side (95% sure on this). I cannot, however, get MPD to connect to the stream. The service I am using to push the music is ampache. Server OS is Intrepid Server; Client is Intrepid Desktop. Both are i386. This obviously means I'm working with two machines, with MPD not on the server machine. Neither machine is behind a router, and the DHCP addresses are the external IPs.

Here is what my MPD.conf file looks like:

```
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory         "/var/lib/mpd/music"
playlist_directory      "/var/lib/mpd/playlists"
db_file                 "/var/lib/mpd/tag_cache"
log_file                "/var/log/mpd/mpd.log"
error_file              "/var/log/mpd/errors.log"
pid_file                "/var/run/mpd/pid"
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file              "/var/lib/mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "mpd"
#
# The address and port to listen on.
#
bind_to_address                 "any"
port                            "4800"
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
#mixer_type                      "alsa"
#mixer_device                    "default"
#mixer_control                   "PCM"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#[CODE]
```
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
################################################################[/CODE]

I know that's kind of long, but I'm note sure if there is anything in there that is messing with it, or that I need to further modify. The only changes I have made are to the bind_to_address. I have tried this using "any", as well as my IP address.

After I made this change to the mpd.conf file, I did this:

```
root@CFreeman-PC:~# vi /etc/mpd.conf
root@CFreeman-PC:~# /etc/init.d/mpd restart
 * Stopping Music Player Daemon mpd                                                                                                   [ OK ] 
 * Starting Music Player Daemon mpd                                                                                                          No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed

```

Does anyone have any ideas?

---

### Post by mikezila on 2009-05-09
Gotta start /etc/init.d/mpd with sudo.

Also, what sound output system (alsa, pulse, OSS, etc) do you use?  Sometimes MPD's best guess doesn't cut it.

---

### Post by cfree220 on 2009-05-12
Yeah, I later discovered that the "best guess" was not working and configured it to use ALSA.

The only problems that are outstanding with the setup are that:

1. When binding on it's external IP address, you have to manually change the config whenever you change your connection (e.g. bind to my school IP vs my home IP). During startup, I get an error saying that MPD cannot listen on port 6600... I think this may have something to do with the listening address being wrong, but I'm not quite sure.

2. The other problem that I have is the sound quality when pushing .flac files using Ampache's localplay where the server is not on the same machine as the MPD instance. I'm not sure if this is an MPD issue or not... when trying to play a .flac, there will be no sound for several seconds followed by an unpleasant, high-pitched sound.

---

### Post by mikezila on 2009-05-12
You can fix number one by not specifying any address at all.  Just leave that line "bind_to_address", I think, commented, or set it to "any", and it'll bind to any and all addresses available when it starts.  I had this exact problem, and this fixed it.  It'll make it so that you can connect with localhost, your hostname, your IP, anything that "should work" will work, instead of just what you configure.

Don't know about number 2.

As a friendly reminder (because I forget all the time too) man pages will be able to help you 8 times out of 10.  You can do "man mpd" or "man mpd.conf" to learn more about how MPD works and how to fill out it's config files.

---

