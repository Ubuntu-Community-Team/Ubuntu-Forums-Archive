---
title: "Sansa Clip (mp3 player).Can create playlists in WindowsMediaPlay but can't in Ubuntu?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by hanzj on 2009-09-02
Hello,
Sansa Clip user manual 
( [http://www.sansa.com/sites/default/files/downloads/CLIP_UM_0608_ENG.pdf](http://www.sansa.com/sites/default/files/downloads/CLIP_UM_0608_ENG.pdf) , particularly, pages 9-12)
says one can create playlists using Windows Media Player. 

But how can I create playlists in Ubuntu?

Thanks.

---

### Post by mikechant on 2009-09-02
The instructions you link to don't give any details about the format of the playlists. However, the most common sort in my experience is the 'm3u' playlist.
Essentially this is just a text file called whateveryoulike.m3u containing a list of track names (assuming the playlist is in the same folder as the tracks).
I'm not at my Ubuntu PC at present but if I remember correctly, the program 'kid3' in addition to its main function - editing the tags on mp3 (and other music) files it can automatically generate an m3u playlist from a selection of tracks. Most CD ripping programs can also generate m3u playlists automatically.

Later: I've checked out Windows Media Player playlists, and naturally being Microsoft, they use their own (xml-based) format for playlists (.wpl files). You could try m3u playlists to see if they work - microsoft used to use them in earlier versions of WMP.

---

### Post by hanzj on 2009-09-02
i tried 
easytag, as per the advice on [http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=4410](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=4410)


I followed the instructions there, namely:> 
1. Connect the Clip to the PC in MSC mode(this is default in Linux).
2. Open EasyTAG and browse to the music folder of the Clip. In my case it was /media/SANSA M340/MUSIC. ( I had just one folder under MUSIC and it was named 'Running Assorted' and it contained all my music files). Your music collection should show up in the midle pane.
3. Select the Files you want to create into a playlist in the middle pane of EasyTAG. (You can also make ID3 tag changes to the music files if you want)
4. Once selected, Click on the 'Write Playlist' icon in the toolbar (third from right).
5. The 'Generate A Playlist' window should now pop-up. This is the important part , ensure the choices you make here are similar to mine.
5a. M3U Playlist Name : Choose "_Use mask_" and give it a name. Example: "test" ( no need for file extension)
5b. Playlist Options: Ensure "_Include only the selected files_" is selected.
5c. Ensure "_Use relative path for files in playlist_" is selected.
5d. Ensure "_Create playlist in the parent directory_" is selected.
5e. Ensure "_Use DOS directory selector_" is selected.
5f. Playlist Content: Select "[COLOR=#ff0000]_Write info using filename_[/COLOR]".
6. Click on "Save" button.
7. You should now have a playlist file named test.m3u in the MUSIC folder.
8. Unmount the device and check if the playlist is showing up now.
I looked at my "testing.m3u" file, and it looks like this:
> 
#EXTM3U 
#EXTINF:382,beethoven-14-2-1.mp3 
music\classical\beethoven\sonata_no.10_in_G_major\beethoven-14-2-1.mp3 
#EXTINF:278,18 Paid It All.mp3 
music\cov_life\18 Paid It All.mp3 
#EXTINF:129,othedeep_high.mp3 
music\hymns\othedeep_high.mp3 
#EXTINF:213,thelove_high.mp3 
music\hymns\thelove_high.mp3 

For my purposes, 5f is better if "Write info using:" is selected, with the blank containing > %t

UPDATE: 5f doesn't seem to need changing.

---

### Post by hanzj on 2009-11-05
I was trying to add an mp3 to a playlist using the methods I described. I tried tinkering with the different options on the Save Playlist dialog window of EasyTag. Nothing worked. Then, with the Sansa Clip disconnected, I tried to locate the mp3 on the Clip, using Album and Title. But it wasn't there. Puzzled, I plugged it in and checked the contents using Ubuntu's file browser (Nautilus). The mp3 *was* indeed there. So why wasn't any of my playlist methods working?

I figured it out. The mp3 I downloaded was set in the Audiobooks genre (Therefore the mp3 was listed in its own special category of "Audiobooks" , and is not listed with the other mp3s on the Clip).When I changed that to something else (e.g. Spoken Word), the playlist thing worked.

In conclusion, audiobook-genre MP3s don't appear in regular listings and can't be added to playlists.

---

### Post by SteveNorman on 2009-11-27
I know you said this is solved, but you can use ID3 to add tags for playlists manually, so they will show up in your menu.


[http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=13972](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=13972)

---

