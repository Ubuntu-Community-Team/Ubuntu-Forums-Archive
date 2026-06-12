---
title: "Convert wbz files to jpg"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by dhiman33 on 2010-11-20
#-oCan someone tell me the way to convert wbz files to jpg in ubuntu? :rolleyes:The process should retain the title and the metadata of the original picture. I've tried xnview; but it can't show the actual title of the image, also for some weird reason it's giving garbled picture as output for the last 2 days!](*,)Then I tried wbz2jpg, and it only shows the title:evil:, doesn't convert the image at all! Now I've downloaded kuwc; and.... OMG[-X it's for kde and so I have to download over 50 mb of software to do this simple task!!! so is there a really easy way to do this simple job?

---

### Post by ronnielsen1 on 2010-11-20
I've never heard of a wbz extension but if I want to change extensions of photos (example jpg) I use gimp, it works great. Try it and see if it works.

---

### Post by ronnielsen1 on 2010-11-22
any luck?

---

### Post by dhiman33 on 2010-11-22
:xI always new gimp or something like that won't be able to open/convert webshots(.wbz) files, still I went to search google and found this--- "http://www.gimphelp.org/formats.shtml"---the link clearly states that gimp can't read wbz files.[-(:cry:


P.S: In case u people don't know what are .wbz files--- these are picture formats downloaded from webshots.com---they can be opened with the "webshots desktop" application in windows, or converted easily using "ultimate webshots converter". But I can't find any good software in linux to do the conversion.(And I'm not gonna use kuwc as that's going to download abt 50 mb kde things for it to work).

---

### Post by dhiman33 on 2010-11-24
):PHello, someone wants to reply?:confused:

---

### Post by MrWES on 2010-11-24
> **dhiman33 said:**
> #-oCan someone tell me the way to convert wbz files to jpg in ubuntu? :rolleyes:The process should retain the title and the metadata of the original picture. I've tried xnview; but it can't show the actual title of the image, also for some weird reason it's giving garbled picture as output for the last 2 days!](*,)Then I tried wbz2jpg, and it only shows the title:evil:, doesn't convert the image at all! Now I've downloaded kuwc; and.... OMG[-X it's for kde and so I have to download over 50 mb of software to do this simple task!!! so is there a really easy way to do this simple job?

Came across this link. It appears you need to compile the source code. It's not that big and might be worth the try.

[http://dan.hersam.com/2005/05/04/convert-webshots-files-to-jpegs-in-linux/]("http://dan.hersam.com/2005/05/04/convert-webshots-files-to-jpegs-in-linux/")

Bill

---

### Post by dhiman33 on 2010-11-25
\\:D/Hey MrWES that works! Only with a little dissatisfaction[-(----to convert in this method, I have to type"wbz2jpg input.wbz output.jpg"---u see that the name of the output jpg is given by me:-?, and it's not the original name of the picture. Also I don't think the extra info's of the picture is saved[-(. Anything to solve this?

P.S.---I went to nautilus actions config. and entered the path of the program-- and in parameters "%M %M.jpg". Now "Convert to jpg" appears in the rt. click menu of wbz files!!

---

### Post by MrWES on 2010-11-25
Read post #11 on that link. There is a small bash script that apparantly will take care of the naming issue.

Bill

Oh...BTW,you don't need to use output.jpg, you can use the original name.

Read post #55 on this link:
[http://ubuntuforums.org/showthread.php?t=91377&page=6]("http://ubuntuforums.org/showthread.php?t=91377&page=6")

---

### Post by dhiman33 on 2010-11-25
Nothing happens by running those things---- pls tell me what to do in more details----I even don't know what is a script and how that works.

---

### Post by dhiman33 on 2010-11-25
Pls someone tell me a way, I think I'm on the verge of success but still can fully grasp it. I think I'm not able to run those scripts in a proper way. I've added them to the rt. click menu but nothing happens....

---

### Post by dhiman33 on 2010-11-26
Hello....:confused:

---

### Post by dhiman33 on 2010-11-26
Hello.... anyone willing to respond?:confused:

---

### Post by dhiman33 on 2010-11-26
O.k MrWES, now I've reviewed that scripts and here's what I found out. The post #55 is useless for me as it's only for the purpose of converting more than one file at a time. Post #11 in the other link actually tries to achieved the naming issue, but for some reason, it's also not working....I've both wbz2jpg &wbzd in the same folder as the script and still nothing happens. Can someone review the script to see if it contains some error(I don't understand script-things!).Here's the script---

#!/bin/sh
# You need the wbz2jpg and wbzd in this directory (if not, take out the “.”)

if [ "$1" = "" ]; then
echo Usage: $0 filename.wbz
exit 1
fi

./wbz2jpg $1 `./wbzd $1`

So why it doesn't work?

---

### Post by HermanAB on 2010-11-26
Howdy,

There is a utility called 'convert' which is part of the Image Magick package.  It can convert any kind of image.  Read the man page.

---

### Post by MrWES on 2010-11-26
did you make the scripts executable? Right mouse click on the script file and put a tick mark in execute as a program, or from the terminal type:

```
chmod u+x scriptname.sh
``` or whatever.

Bill

---

### Post by dhiman33 on 2010-11-27
;)Yes ofcourse MrWES. I made that one executable before entering it's path in nautilus actions. Do u think that script is o.k?

P.S---And I'm gonna see that "convert" thing too...

---

### Post by dhiman33 on 2010-11-27
I can't find the "convert" utility there herman. BTW, I think now I can mark this thread as solved as I have received atleast 80% success....I can get the name of jpg by wbzd, can convert the wbz file using wbz2jpg, and then can rename it manually...problem is mostly solved.(Though that script doesn't work)

---

### Post by shearerc on 2011-04-10
i was looking for a solution for this
thanks so much!

---

### Post by Stryker777 on 2011-05-14
I used the following:
[http://pastebin.com/f77e4e93c](http://pastebin.com/f77e4e93c)

I saved the code as convertwbz and ran it like this:
./convertwbz ImageName.wbz

It takes the picture title and makes it the file name.

In case the code is no longer there:

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
import sys
import os, struct, array

K_TITLE = "title"
K_CREDITS = "credits"
K_ID = "id"
K_ALBUM = "album"
K_FILENAME = "filename"
K_DESCRIPTION = "description"

def strip(text):
    '''
    Strip a string by removing not only whitespaces but also all the final 0x0

    @param text: the string to strip
    '''
    pos = text.find(chr(0))
    if pos >= 0:
        text = text[:pos]
    return text.strip()

class Data(object):
    """
    A convenient object where attributes can be added dynamically
    """
    pass

class Pixmap(object):
    """
    This class is the base object manipulated by these file:
    - an image
    - the JPEG data
    - the info about the image

    The image is a Array of bits representing the JPEG data
    The info is a dictionary of key (K_XX), texts
    """
    def __init__(self):
        """
        Constructor
        """
        self.jpeg = array.array('B')
        self.info = {}
        
    def getJPEGSize(self):
        '''
        @return the size of the image directly from the JPEG data
        '''
        idata = iter(self.jpeg)
        width = None
        height = None
        try:
            B1 = idata.next()
            B2 = idata.next()
            if B1 != 0xFF or B2 != 0xD8:
                return -1, -1
            while True:
                byte = idata.next()
                while byte != 0xFF:
                    byte = idata.next()
                while byte == 0xFF:
                    byte = idata.next()
                if byte >= 0xc0 and byte <= 0xc3:
                    idata.next()
                    idata.next()
                    idata.next()
                    height, width = struct.unpack('>HH',"".join(chr(idata.next()) for b in range(4)) ) #@UnusedVariable
                    break
                else:
                    offset = struct.unpack('>H', chr(idata.next()) + chr(idata.next()))[0] - 2
                    for _ in xrange(offset):
                        idata.next()
        except StopIteration:
            pass
        return (width, height)

class WB1(object):
    """
    This class allows to read wb1, wbd and wbz files
    """
    MAGIC_WB1_NOT_ENCODED = 0xE0FFD8FF
    MAGIC_WB1_ENCODED = 0x42425757
    MAGIC_WBZ = 0x6791AB43
    FILE_MARKER = 0x1082CDE1
    KEY2K = {
        'STR_ImageTitle' :      K_TITLE,
        'title' :               K_TITLE,
        'STR_ImageCredit' :     K_CREDITS,
        'credit' :              K_CREDITS,
        'STR_CollectionTitle' : K_ALBUM,
        'albumTitle' :          K_ALBUM,
        'filename' :            K_FILENAME,
        'FIL_ImageFileName' :   K_FILENAME,
        'id' :                  K_ID,
        }

    @staticmethod
    def read(url, data, buildPixmap = True):
        """
        Read the data and read the image data and info

        @param[in] url the url to the file
        @param[in] data the file data stream
        @param[in] buildPixmap if True build the QPixmap object
        @return a Pixmap image
                None if the magic number of the file does not correspond to the handled types of file
        """
        try:
            pixmap = Pixmap()
            data.seek(0)
            magic = struct.unpack('<I', data.read(4))[0]
            if magic == WB1.MAGIC_WB1_NOT_ENCODED:
                WB1.__decodeWB1(url, data, pixmap, buildPixmap)
            elif magic == WB1.MAGIC_WB1_ENCODED:
                WB1.__decodeWB1_Encoded(url, data, pixmap, buildPixmap)
            elif magic == WB1.MAGIC_WBZ:
                WB1.__decodeWBZ(url, data, pixmap, buildPixmap)
            else:
                return None
            return pixmap
        except:
            return None
    @staticmethod
    def decodeJPEG(data, pixmap, buildPixmap, fileSize = 0):
        """
        Decode the encoded JPEG data

        @param[in] data the file data stream, it must be positioned at the beginning of the encoded JPEG data
        @param[in,out] pixmap the Pixmap instance that will contain the image
        @param[in] buildPixmap if True build the QPixmap object
        @param[in] fileSize the size of the JPEG data. If 0, read them to the end of the file.
        """
        code = data.read(4)
        if code == "0000":
            key = 0xA4
        elif code == "1111":
            key = 0xF2
        else:
            raise Exception("Invalid file format")
        if fileSize:
            pixmap.jpeg.fromfile(data, fileSize)
        else:
            try:
                # read bits until EOF
                while True:
                    pixmap.jpeg.fromfile(data, 0x4000)
            except EOFError:
                pass
        # decode the image (NB '~x' returns a negative integer so we use 'x ^ 0xFF' instead)
        for i in xrange(100):
            pixmap.jpeg[i] = (pixmap.jpeg[i + 100] ^ (0xFF ^ pixmap.jpeg[i])) ^ key
        if buildPixmap:
            # check that the data are valid
            if not pixmap.pixmap.loadFromData(pixmap.jpeg.tostring()):
                raise Exception("Invalid file format")
    @staticmethod
    def readJPEG(data, pixmap, buildPixmap, fileSize = 0):
        """
        Read the JPEG data

        @param[in] data the file data stream, it must be positioned at the beginning of the encoded JPEG data
        @param[in,out] pixmap the Pixmap instance that will contain the image
        @param[in] buildPixmap if True build the QPixmap object
        @param[in] fileSize the size of the JPEG data. If 0, read them to the end of the file.
        """
        if fileSize:
            pixmap.jpeg.fromfile(data, fileSize)
        else:
            try:
                # read bits until EOF
                while True:
                    pixmap.jpeg.fromfile(data, 0x4000)
            except EOFError:
                pass
        if buildPixmap:
            # check that the data are valid
            if not pixmap.pixmap.loadFromData(pixmap.jpeg.tostring()):
                raise Exception("Invalid file format")
    @staticmethod
    def __decodeWB1(url, data, pixmap, buildPixmap):
        """
        Reads the contents of a non encoded WB1 file

        @param[in] url the url to the file
        @param[in] data the stream to the file data positioned just after the 4 bytes of the magic number
        @param[in] buildPixmap if True build the QPixmap object
        @param[out] pixmap the resulting array of bytes
        """
        WB1.readJPEG(data, pixmap, buildPixmap)
        pixmap.info.update(PhotosInfo.parse(url).get(url))
        pixmap.info.update(AlbumInfo.parse(url).get())
    @staticmethod
    def __decodeWB1_Encoded(url, data, pixmap, buildPixmap):
        """
        Reads the contents of an encoded WB1 file

        @param[in] url the url to the file
        @param[in] data the stream to the file data positioned just after the 4 bytes of the magic number
        @param[in] buildPixmap if True build the QPixmap object
        @param[out] pixmap the resulting array of bytes
        """
        WB1.decodeJPEG(data, pixmap, buildPixmap)
        pixmap.info.update(PhotosInfo.parse(url).get(url))
        pixmap.info.update(AlbumInfo.parse(url).get())
    @staticmethod
    def __decodeWBZ(url, data, pixmap, buildPixmap): #@UnusedVariable
        """
        Reads the contents of a WBZ file

        @param[in] url the url to the file
        @param[in] data the stream to the file data positioned just after the 4 bytes of the magic number
        @param[in] buildPixmap if True build the QPixmap object
        @param[out] pixmap the resulting Pixmap
        """
        # JPEG data
        firstFileOffset = struct.unpack('<I', data.read(4))[0]
        data.seek(firstFileOffset)
        includedFileMarker = struct.unpack('<I', data.read(4))[0]
        if includedFileMarker != WB1.FILE_MARKER:
            raise Exception(i18n("Invalid file format"))
        headerSize = struct.unpack('<I', data.read(4))[0]
        data.read(4)
        data.read(256) # fileName
        fileSize = struct.unpack('<I', data.read(4))[0]
        data.read(264)
        code = data.read(4)
        if (code == "WWBB"):
            WB1.decodeJPEG(data, pixmap, buildPixmap, fileSize-8)
        else:
            data.seek(firstFileOffset + headerSize)
            WB1.readJPEG(data, pixmap, buildPixmap, fileSize)
        # description (an INI style file)
        includedFileMarker = struct.unpack('<I', data.read(4))[0]
        if includedFileMarker == WB1.FILE_MARKER:
            headerSize = struct.unpack('<I', data.read(4))[0]
            data.read(4)
            data.read(256) # fileName
            fileSize = struct.unpack('<I', data.read(4))[0]
            data.read(264)
            bytes = data.read(fileSize)
            for line in bytes.splitlines():
                try:
                    key, val = line.split('=',1)
                    k = WB1.KEY2K.get(key, None)
                    if k:
                        pixmap.info[k] = val
                except:
                    pass

class WBC(object):
    """
    This class allows to reab wbc files
    """
    MAGIC_WBC = 0x95FA16AB
    PB_MARKER  = 0xF071CDE2

    @staticmethod
    def read(path, data, buildPixmap = True):
        """
        Read the data and read the image data and info

        @param[in] path the path to the file
        @param[in] data the file data stream
        @param[in] buildPixmap if True build the QPixmap objects
        @return (title, pixmaps) where title is the file title and pixmaps is an array of Pixmap
                (None, None) if the magic number of the file does not correspond to the handled types of file
        """
        try:
            pixmaps = []
            title = ""
            data.seek(0, 2)
            data_size = data.tell()
            data.seek(0)
            magic = struct.unpack('<I', data.read(4))[0]
            if magic == WBC.MAGIC_WBC:
                title = WBC.__decodeWBC(path, data, data_size, pixmaps, buildPixmap)
            else:
                return (None, None)
            return (title, pixmaps)
        except:
                return (None, None)

    @staticmethod
    def __decodeWBC(path, data, data_size, pixmaps, buildPixmap): #@UnusedVariable
        """
        Reads the contents of a non encoded WB1 file

        @param[in] path the path to the file
        @param[in] data the stream to the file data positioned just after the 4 bytes of the magic number
        @param[in] data_size the size of the file
        @param[out] title the file title
        @param[out] pixmaps the resulting array of Pixmap
        @param[in] buildPixmap if True build the QPixmap objects
        @return the title of the collection
        """
        struct.unpack('<I', data.read(4))[0] # firstPBOffset
        data.read(4)
        title = strip(data.read(89))
        data.seek(2196)
        nimages = struct.unpack('<I', data.read(4))[0]
        headers = []
        for i in xrange(nimages): #@UnusedVariable
            hImg = Data()
            hImg.PBOffset = struct.unpack('<I', data.read(4))[0]
            hImg.PBSize = struct.unpack('<I', data.read(4))[0]
            data.read(4)
            hImg.PBAdditionDate = struct.unpack('<I', data.read(4))[0]
            data.read(24)
            headers.append(hImg)
        for h in headers:
            pixmap = Pixmap()
            pixmap.info[K_ALBUM] = title
            # read the header
            data.seek(h.PBOffset)
            PBMarker = struct.unpack('<I', data.read(4))[0]
            headerSize = struct.unpack('<I', data.read(4))[0]
            PBSize = struct.unpack('<I', data.read(4))[0]
            pixmap.info[K_FILENAME] = strip(data.read(256))
            pixmap.info[K_TITLE] = strip(data.read(128))
            pixmap.info[K_DESCRIPTION] = strip(data.read(256))
            pixmap.info[K_CREDITS] = strip(data.read(256))
            data.read(8) # originalFileExtension
            JPGFileSize = struct.unpack('<I', data.read(4))[0]
            data.read(4) # BMPFileSize
            data.read(140)
            data.read(4) # dailyDate
            data.read(4) # additionDate
            data.read(4) # fitToScreen
            pixmap.info[K_ID] = strip(data.read(128))
            data.read(96) # childCategory
            data.read(788) # rootCategory
            # read the image
            if (PBMarker != WBC.PB_MARKER) or (h.PBOffset + PBSize > data_size):
                continue
            data.seek(h.PBOffset + headerSize)
            code = data.read(4)
            if (code == "WWBB"):
                WB1.decodeJPEG(data, pixmap, buildPixmap, JPGFileSize-8)
            else:
                data.seek(h.PBOffset + headerSize)
                WB1.readJPEG(data, pixmap, buildPixmap, JPGFileSize)
            #
            pixmaps.append(pixmap)
        return title



for li in sys.argv[1:]:
    print "Now processing %s..." % li
    # let's process it
    try:
        f = open(unicode(li), 'rb')
    except IOError:
        print "IOError opening %s" % li

    try:
        # let's try first a WB[1DZ] file
        pixmap = WB1.read(li, f, buildPixmap = False)
        if pixmap:
            pixmaps = [ pixmap ]
        else:
            # let's try a WBC file
            title, pixmaps = WBC.read(li, f, buildPixmap = False) #@UnusedVariable
    finally:
        del f
    # now let's save the files
    for pixmap in pixmaps:
    # build the output file name
        fnu = pixmap.info.get(K_TITLE, "image") + ".jpg"
        fn = unicode(fnu, 'latin-1');
        # now save it
        of = open(fn, "wb")
        print "Saved %s" % fnu
        try:
            pixmap.jpeg.tofile(of)
        finally:
            of.close()

```

---

