---
title: "Adding VIDEO info columns (e.g. resolution, etc.) to nautilus list view"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by hopelessone on 2009-10-04
Hi All,

This post coveres the MP3 tags...
[http://ubuntuforums.org/showthread.php?t=878683](http://ubuntuforums.org/showthread.php?t=878683)

Does anyone know how to do this for Movie files?

.avi .mpg .vob etc...

So Far I've got:

```
#!/usr/bin/python
# this script can installed to the current user account by running the following commands:

# sudo apt-get install python-nautilus python-mutagen python-pyexiv2 
#sudo apt-get install python-kaa-metadata
# mkdir ~/.nautilus/python-extensions
# cp bsc-v2.py ~/.nautilus/python-extensions
# chmod a+x ~/.nautilus/python-extensions/bsc-v2.py

# alternatively, you may be able to place the script in:
# /usr/lib/nautilus/extensions-2.0/python/

# change log:
# jmdsdf: version 2 adds extra ID3 and EXIF tag support
# jmdsdf: added better error handling for ID3 tags, added mp3 length support, distinguished
#         between exif image size and true image size
# SabreWolfy: set consistent hh:mm:ss format, fixed bug with no ID3 information 
#             throwing an unhandled exception
# jmdsdf: fixed closing file handles with mpinfo (thanks gueba)
# jmdsdf: fixed closing file handles when there's an exception (thanks Pitxyoki)
 
import os
import urllib
import nautilus
# for id3 support
from mutagen.easyid3 import EasyID3
from mutagen.mp3 import MPEGInfo
# for exif support
import pyexiv2

# for reading image dimensions
import Image

#for reading video length
import kaa.metadata #It also gives mp3 support I think

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
    def __init__(self):
        pass

    def get_columns(self):
        return (
            # id3 support
            nautilus.Column("NautilusPython::title_column",
                "title",
                "Title",
                "Song title"),
            nautilus.Column("NautilusPython::artist_column",
                "artist",
                "Artist",
                "Artist"),
            nautilus.Column("NautilusPython::album_column",
                "album",
                "Album",
                "Album"),
            nautilus.Column("NautilusPython::tracknumber_column",
                "tracknumber",
                "Track",
                "Track number"),
            nautilus.Column("NautilusPython::genre_column",
                "genre",
                "Genre",
                "Genre"),
            nautilus.Column("NautilusPython::date_column",
                "date",
                "Date",
                "Date"),
            nautilus.Column("NautilusPython::bitrate_column",
                "bitrate",
                "Bitrate",
                "Audio Bitrate in kilo bits per second"),
            nautilus.Column("NautilusPython::length_column",
                "length",
                "Length",
                "Length of audio"),
nautilus.Column("NautilusPython::dimensions_column",
                "dimensions",
                "Dimensions",
                "Dimensions"),
            # exif support
            nautilus.Column("NautilusPython::exif_datetime_original_column",
                "exif_datetime_original",
                "EXIF Dateshot ",
                "Get the photo capture date from EXIF data"),
            nautilus.Column("NautilusPython::exif_software_column",
                "exif_software",
                "EXIF Software",
                "EXIF - software used to save image"),
            nautilus.Column("NautilusPython::exif_flash_column",
                "exif_flash",
                "EXIF flash",
                "EXIF - flash mode"),
            nautilus.Column("NautilusPython::exif_pixeldimensions_column",
                "exif_pixeldimensions",
                "EXIF Image Size",
                "EXIF Image size - pixel dimensions"),
            nautilus.Column("NautilusPython::pixeldimensions_column",
                "pixeldimensions",
                "Image Size",
                "Image size - pixel dimensions"),  
        )

    def update_file_info(self, file):
        if file.get_uri_scheme() != 'file':
            return

        filename = urllib.unquote(file.get_uri()[7:])
        
        # video handling
        if file.is_mime_type('video/x-msvideo'):
            viinfo=kaa.metadata.parse(filename)
            vilength = "%02i:%02i:%02i" % ((int(viinfo.length/3600)), (int(viinfo.length/60%60)), (int(viinfo.length%60)))
            file.add_string_attribute('length',vilength) 
	file.add_string_attribute('dimensions',vilength)   
        else:
            pass
        
        # mp3 handling
        if file.is_mime_type('audio/mpeg'):
            # attempt to read ID3 tag
            try:
                audio = EasyID3(filename)
                # sometimes the audio variable will not have one of these items defined, that's why
                # there is this long try / except attempt
                try:
                    file.add_string_attribute('title', audio["title"][0])
                except:
                    file.add_string_attribute('title', "[n/a]")
                try:
                    file.add_string_attribute('album', audio["album"][0])
                except:
                    file.add_string_attribute('album', "[n/a]")
                try:
                    file.add_string_attribute('artist', audio["artist"][0])
                except:
                    file.add_string_attribute('artist', "[n/a]")
                try:
                    file.add_string_attribute('tracknumber', audio["tracknumber"][0])
                except:
                    file.add_string_attribute('tracknumber', "[n/a]")
                try:
                    file.add_string_attribute('genre', audio["genre"][0])
                except:
                    file.add_string_attribute('genre', "[n/a]")
                try:
                    file.add_string_attribute('date', audio["date"][0])
                except:
                    file.add_string_attribute('date', "[n/a]")
            except:
                # [SabreWolfy] some files have no ID3 tag and will throw this exception:
                file.add_string_attribute('title', "[no ID3]")
                file.add_string_attribute('album', "[no ID3]")
                file.add_string_attribute('artist', "[no ID3]")
                file.add_string_attribute('tracknumber', "[no ID3]")
                file.add_string_attribute('genre', "[no ID3]")
                file.add_string_attribute('date', "[no ID3]")
                
            # try to read MP3 information (bitrate, length)
            try:
                mpfile = open (filename)
                mpinfo = MPEGInfo (mpfile)
                file.add_string_attribute('bitrate', str(mpinfo.bitrate/1000) + " Kbps")
                # [SabreWolfy] added consistent formatting of times in format hh:mm:ss
                # [SabreWolfy[ to allow for correct column sorting by length
                mp3length = "%02i:%02i:%02i" % ((int(mpinfo.length/3600)), (int(mpinfo.length/60%60)), (int(mpinfo.length%60)))
                mpfile.close()
                file.add_string_attribute('length', mp3length)
            except:
                file.add_string_attribute('bitrate', "[n/a]")
                file.add_string_attribute('length', "[n/a]")
                try:
                    mpfile.close()
                except:    pass

        else:
            # not a song
            file.add_string_attribute('title', '')
            file.add_string_attribute('album', '')
            file.add_string_attribute('artist', '')
            file.add_string_attribute('tracknumber', '')
            file.add_string_attribute('genre', '')
            file.add_string_attribute('date', '')
            file.add_string_attribute('bitrate', '')
            if file.is_mime_type('video/x-msvideo'):
                pass
            else:
                file.add_string_attribute('length', '')
        
        # image handling
        if file.is_mime_type('image/jpeg') or file.is_mime_type('image/png') or file.is_mime_type('image/gif') or file.is_mime_type('image/bmp'):
            # EXIF handling routines
            try:
                img = pyexiv2.Image(filename)
                img.readMetadata()
                file.add_string_attribute('exif_datetime_original',str(img['Exif.Photo.DateTimeOriginal']))
                file.add_string_attribute('exif_software',str(img['Exif.Image.Software']))
                file.add_string_attribute('exif_flash',str(img['Exif.Photo.Flash']))
                file.add_string_attribute('exif_pixeldimensions',str(img['Exif.Photo.PixelXDimension'])+'x'+str(img['Exif.Photo.PixelYDimension']))
            except:
                # no exif data?
                file.add_string_attribute('exif_datetime_original',"")
                file.add_string_attribute('exif_software',"")
                file.add_string_attribute('exif_flash',"")
                file.add_string_attribute('exif_pixeldimensions',"")
            # try read image info directly
            try:
                im = Image.open(filename)
                file.add_string_attribute('pixeldimensions',str(im.size[0])+'x'+str(im.size[1]))
            except:
                file.add_string_attribute('pixeldimensions',"[image read error]")
        else:
            # not an image
            file.add_string_attribute('exif_datetime_original', '')
            file.add_string_attribute('exif_software', '')
            file.add_string_attribute('exif_flash', '')
            file.add_string_attribute('exif_pixeldimensions', '')
            file.add_string_attribute('pixeldimensions', '')
        
        self.get_columns()
```

Theres 2 things i can't do yet:

Change [COLOR="Red"]vilength[/COLOR] into reading **video dimensions**..

```
**vilength = "%02i:%02i:%02i" % ((int(viinfo.length/3600)), (int(viinfo.length/60%60)), (int(viinfo.length%60)))**
```

```
**file.add_string_attribute('dimensions',[COLOR="Red"]vilength[/COLOR]) **
```

Thanks

---

### Post by hopelessone on 2009-10-04
Can you help me impliment this into nautulis?
[http://www.daniweb.com/forums/thread29495.html#](http://www.daniweb.com/forums/thread29495.html#)
```
# this python function gets the <strong class="highlight">dimensions</strong> of a <strong class="highlight">video</strong> file and returns them as a tuple (width,height)
# it uses the <strong class="highlight">linux</strong> <strong class="highlight">video</strong> program avitype (I think this is part of the transcode package)

# getdimensions.py

def getdimensions(video_file):

    import commands
    avitype_command= "/usr/bin/avitype %s | grep WxH" % video_file
    <strong class="highlight">dimensions</strong> = commands.getoutput(avitype_command)
    width = <strong class="highlight">dimensions</strong>[-7:-4]
    height = <strong class="highlight">dimensions</strong>[-3:]
    WxH = (width,height)
    return WxH
```

---

### Post by hopelessone on 2009-10-05
*bump*

---

### Post by hopelessone on 2009-10-25
*bump*

---

