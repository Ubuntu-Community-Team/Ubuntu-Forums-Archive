---
title: "MPD and Firefox"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by chessercizes on 2011-01-09
Hey everyone,

So I just got MPD working and I love it! The only problem I have is that if I have my mpd client (ncmpcpp) running, and then I go to open firefox and navigate to a video on youtube, the mpd client seems to "hog" the audio output. The flash video can't play audio.

When i stop the song playing on mpd, the flash video can playaudio again, but now MPD is unable to play anything until I close the actual youtube tab on firefox. It's almost like only one of them is allowed to play audio at a time, and they fight for it and both hog it.

I've posted my /etc/mpd.conf file below (with all commented lines removed).

```

music_directory			"/home/parth/Music/"
playlist_directory		"/var/lib/mpd/playlists"
db_file			        "/var/lib/mpd/tag_cache"
log_file			"/var/log/mpd/mpd.log"
pid_file			"/var/run/mpd/pid"
state_file			"/var/lib/mpd/state"
bind_to_address		        "127.0.0.1"

input {
        plugin "curl"
}

audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,0"	# optional
	format		"44100:16:2"	# optional
	mixer_device	"default"	# optional
	mixer_control	"PCM"		# optional
	mixer_index	"0"		# optional
}

mixer_type			"software"

filesystem_charset		"UTF-8"
id3v1_encoding			"UTF-8"

```

Any suggestions on how to make it so that mpd doesn't hog the audio output? Thank you very much for any help!

---

### Post by jacksonpollack on 2011-03-08
It's a conflict with PulseAudio when you are running mpd as user "mpd," not as an actual user. There's probably a real solution out there, but if you configure mpd to run as your user name, you can work around the problem. See here:
[http://askubuntu.com/questions/29029/mpd-conflicting-with-other-applications-taking-control-of-pulse](http://askubuntu.com/questions/29029/mpd-conflicting-with-other-applications-taking-control-of-pulse)

---

