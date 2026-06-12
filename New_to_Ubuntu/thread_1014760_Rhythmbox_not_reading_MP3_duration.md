---
title: "Rhythmbox not reading MP3 duration"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-18
I've got about 50 MP3 songs on my Ubuntu 8.10 laptop... now i'm wondering why my Rythmbox doesn't have the duration bar running when playing alot of these mp3 titles eventhough when i right click on the files themselves (under properties and it shows the length of the song and other information)

has anyone experience this with Rhythmbox? and how can i fix this?
cheers

---

### Post by por100pre1 on 2008-12-18
Maybe the way those mp3 files is causing the issue. **Make a backup copy of those mp3 files** and encode them files using soundconverter. Let us know if that works. **Just be sure to backup your files first.**

---

### Post by lucasl on 2008-12-18
This can be cause by improper VBR encoding. A better way then reencoding is to use the vbrfix program (in the repos I believe), because it doesn't reencode (which loses quality), only fixes the length.
It won't do anything if it is a different problem though.

---

### Post by manuleka on 2008-12-19
so how do i use this program? i've installed it through synaptic and i can't see where to run the program from...

---

### Post by vanadium on 2008-12-19
It is a console application. Type "man vbrfix" for the manual page. Executing the command without arguments ("vbrfix") displays a short help screen.

---

### Post by manuleka on 2008-12-19
is there a gui version of this vbrfix program?

---

### Post by vanadium on 2008-12-19
Would you need that? What is the difficulty in typing "vbrfix in.mp3 out.mp3"?

Install nautilus-open-terminal using Synaptic
Navigate to the directory where your mp3's are. Right-click, select "Open in terminal"
A terminal opens with the directory where your mp3's are as the current working directory (you can tell looking at the prompt.

Type "vbr" (without the quotes) then press the tab key. The shell will expand the name to vbrfix, to save you some typing. Type the first letters of the mp3 you need fixed, and use tab again to have bash autocomplete your entry. Fill the name again, but change it a little, or add a path before it, e.g. "vbrfix in.mp3 fixed/in.mp3". You must create a directory first.

To do all files in the directory:

mkdir fixed
for f in *.mp3 ;  do vbrfix "$f" "fixed/$f" ; done

---

### Post by manuleka on 2008-12-19
i'm a real newbie so i'm not familiar at all with commandline - so if you could be abit more explanatory on those codes would appreciate it thanks :)

edit:

managed to do it on commandline... vbrfix couldn't fix the files... it reports "UNKNOWN FLAG" :(

another note: when i play the songs the time ticks... the only problem is the time bar doesn't move... that happens to the UNKNOWN FLAG songs only :(

---

### Post by vanadium on 2008-12-20
Better copy/paste the command line and its output here if you want to tell what happened.

---

### Post by manuleka on 2008-12-20
VbrFix Command Line Version
===========================
By William Pye, visit [www.willwap.co.uk](www.willwap.co.uk) for latest version
UNKNOWN FLAG ::01 - track 1.mp3
UNKNOWN FLAG ::02 love hurts.mp3
UNKNOWN FLAG ::03 - track 3.mp3
UNKNOWN FLAG ::04 tongan - fakamahino.mp3
UNKNOWN FLAG ::04 - track 4.mp3
UNKNOWN FLAG ::09 - track 9(2).mp3
UNKNOWN FLAG ::10 - track 10(2)(3).mp3
UNKNOWN FLAG ::10 - track 10.mp3
UNKNOWN FLAG ::11 tokelau to i mui fonua(tongan reggae 3).mp3
UNKNOWN FLAG ::11 - track 11.mp3
UNKNOWN FLAG ::12-the_bamboos-tongan_steel.mp3
UNKNOWN FLAG ::13 tongan reggae 13.mp3
UNKNOWN FLAG ::13 - track 13.mp3
UNKNOWN FLAG ::14 tongan reggae- teu talanoa kihe utu longoa_a.mp3
UNKNOWN FLAG ::15 tongan reggae 15.mp3
UNKNOWN FLAG ::18 - track 18.mp3
UNKNOWN FLAG ::1st Lady - Missing You.mp3
UNKNOWN FLAG ::Adeaze - Stronger.mp3
UNKNOWN FLAG ::Alicia Keys - Karma.mp3
UNKNOWN FLAG ::Alicia Keys - When You Really Love Someone.mp3
UNKNOWN FLAG ::Always be my Baby.mp3
UNKNOWN FLAG ::Before you walk out of my Life.mp3
UNKNOWN FLAG ::Bowow - Like You.mp3
UNKNOWN FLAG ::Boyz 2 Men - End of the Road.mp3
UNKNOWN FLAG ::Boyz 2 Men - I'll make love to you.mp3
UNKNOWN FLAG ::Boyz 2 Men - I'll never break your heart.mp3
UNKNOWN FLAG ::Chris Brown ft. Some Chick - Air.mp3
UNKNOWN FLAG ::culture - polynesian - tongan - kapena - ofa loto.mp3
UNKNOWN FLAG ::Day 26 - Cry No More.mp3
UNKNOWN FLAG ::Day 26 - Exclusive (No Excuses).mp3
UNKNOWN FLAG ::Day 26 - Got Me Going.mp3
UNKNOWN FLAG ::Day 26 - You Always.mp3
UNKNOWN FLAG ::dj siemu - alu aipe tongan remix.mp3
UNKNOWN FLAG ::dont say good bye 1.mp3
UNKNOWN FLAG ::Flo-Ryda - Low.mp3
UNKNOWN FLAG ::Fresh of the Boat.mp3
UNKNOWN FLAG ::hawaiian-polynesian - samoan style - tongan reggae 1.mp3
UNKNOWN FLAG ::High School Musical - Breaking Free.mp3
UNKNOWN FLAG ::Homies - Gangster Lean.mp3
UNKNOWN FLAG ::James Morrison - You Gave me Something.mp3
UNKNOWN FLAG ::Jordin Sparks - A Broken Wing.mp3
UNKNOWN FLAG ::Jordin Sparks - Next to You.mp3
UNKNOWN FLAG ::Jordin Sparks - One step at a Time.mp3
UNKNOWN FLAG ::Jordin Sparks - Tattoo.mp3
UNKNOWN FLAG ::Justin Timberlake - Summer Love.mp3
UNKNOWN FLAG ::kirk franklin - god's property - my life is in your hands.mp3
UNKNOWN FLAG ::kontiki - i got someone.mp3
UNKNOWN FLAG ::Lauryn Hill - When it hurts so bad.mp3
UNKNOWN FLAG ::Leona - I have Nothing.mp3
UNKNOWN FLAG ::Leona Lewis - Better in time.mp3
UNKNOWN FLAG ::Leona Lewis - Bleeding Love.mp3
UNKNOWN FLAG ::Leona Lewis - Footprint in the Sand.mp3
UNKNOWN FLAG ::Leona Lewis - Whatever it Takes.mp3
UNKNOWN FLAG ::Leona Lewis - Yesterday.mp3
UNKNOWN FLAG ::Let's Kiss and Say Goodbye.mp3
UNKNOWN FLAG ::Lil Bowow ft. Chris Brown.mp3
UNKNOWN FLAG ::liliani iongi - hiva 'ofa faka-tonga - tongan 'anaua fa'iloka'.mp3
UNKNOWN FLAG ::Lil Jon - Snap your Fingers.mp3
UNKNOWN FLAG ::Lil Wayne ft. Birdman - Stunting Like My Daddy.mp3
UNKNOWN FLAG ::loufatai.mp3
UNKNOWN FLAG ::loveis all we need.mp3
UNKNOWN FLAG ::Luther Vandroos - I'll start back at One.mp3
UNKNOWN FLAG ::malia.mp3
UNKNOWN FLAG ::Maori Boy - Deadly Alliance.mp3
UNKNOWN FLAG ::Mariah Carey - Love takes Time.mp3
UNKNOWN FLAG ::Mariah Carey - Oh No.mp3
UNKNOWN FLAG ::matangi ne angi.mp3
UNKNOWN FLAG ::Matchbox 20 - I only wanna be with you.mp3
UNKNOWN FLAG ::melenau lino - atele collage song.mp3
UNKNOWN FLAG ::Nelly - What's Ya Name.mp3
UNKNOWN FLAG ::Ne-Yo - Do You.mp3
UNKNOWN FLAG ::Ne-Yo - Sexy Love.mp3
UNKNOWN FLAG ::pacific soul - tongan jam.mp3
UNKNOWN FLAG ::pcc - eva ki he kolo salusalu.mp3
UNKNOWN FLAG ::polynesia - tongan - love songs - veitapui.mp3
UNKNOWN FLAG ::Puna and Fontee - AudioTrack 05.mp3
UNKNOWN FLAG ::Rihanna ft. Ne-Yo - Hate That I Love You.mp3
UNKNOWN FLAG ::Samoan Jam - Samoan Wedding Song.mp3
UNKNOWN FLAG ::Seal - I believe i can fly.mp3
UNKNOWN FLAG ::soulja boy - she got a donk.mp3
UNKNOWN FLAG ::The Waifs - London Still.mp3
UNKNOWN FLAG ::TI - What ever you Like.mp3
UNKNOWN FLAG ::tongan - halani si'i mahina.mp3
UNKNOWN FLAG ::tongan love songs- 05-fehu'i by tu'imala kaho.mp3
UNKNOWN FLAG ::tongan-reggae-seku he kakala.mp3
UNKNOWN FLAG ::tongan - si'i lolo.mp3
UNKNOWN FLAG ::tongan - suliasi pole'o - sweet island girl481.mp3
UNKNOWN FLAG ::tongan -tongan-malakai siale - ta'ahine ke ta 'eva.mp3
UNKNOWN FLAG ::Usher - Love in this Club (Remix).mp3
UNKNOWN FLAG ::vbrfix.log
UNKNOWN FLAG ::vbrfix.tmp
UNKNOWN FLAG ::Whitney Houston - I have nothing.mp3
UNKNOWN FLAG ::Whitney Houston - You'll Never Stand Alone.mp3
UNKNOWN FLAG ::Worthy.mp3
FLAGS = 0
Fixing Wyclef ft. Akon - Dollar Dollar.mp3->vbrfix.tmp
FileLength = 7814618
Found Id3v2 tag with size4096
Found [LAME] Xing tag at 4097 with size 417
10%...
20%...
30%...
40%...
Id3v1 tag found
DONE, ABR=260,Frames=9199
CHAN=2
Written new vbr tag
50%...
60%...
70%...
80%...
Copied vbrfix.tmp->Wyclem Jean - You take me as I am.mp3
100%...

what i find is that the timing works... only the timeline bar doesn't function! and only for the UNKNOWN FLAG titles

---

### Post by vanadium on 2008-12-20
You might prefer to re-rip these tracks, but alternatively, try mp3val first to repair the mp3's, then (if still needed), run vbrfix on the mp3val fixed files.

---

### Post by manuleka on 2008-12-20
> **vanadium said:**
> You might prefer to re-rip these tracks, but alternatively, try mp3val first to repair the mp3's, then (if still needed), run vbrfix on the mp3val fixed files.

is this another commanline tool? cheers

---

