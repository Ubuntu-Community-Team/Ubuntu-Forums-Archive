---
title: "is there any software in ubuntu?"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by munna.cheyur on 2010-09-01
i need a software which can read text or which files in .doc format.. thanks in advance.

---

### Post by BrandyBear on 2010-09-01
Use Ubutnu Software center

---

### Post by munna.cheyur on 2010-09-01
how? pls givie its name.

---

### Post by Gone fishing on 2010-09-01
No problem Ubuntu comes with lots of software, Editors, Open office Media players, etc. Thousands of applications are available for free download and easy to find and install using synaptic or Ubuntu software center.

---

### Post by aysiu on 2010-09-01
> **munna.cheyur said:**
> i need a software which can read text or which files in .doc format.. thanks in advance.
Just double-click on the .doc file, and it'll open with OpenOffice. You can also launch OpenOffice by going to Applications > Office > OpenOffice.org Word Processor.

---

### Post by Gone fishing on 2010-09-01
Ubuntu comes with Open Office (office suit compatible with MS Office) gedit and vi (text editors) pre-installed you can download for free Abiword, Koffice, Gnome Office, Vim, Kate etc etc etc

---

### Post by mastablasta on 2010-09-01
> **munna.cheyur said:**
> i need a software which can read text or which files in .doc format.. thanks in advance.
 
Under Applications>Office>**Open Office Writer**. then when you save choose save as Microsoft Word document. This programme can read and write in .doc format.

---

### Post by munna.cheyur on 2010-09-01
> **mastablasta said:**
> Under Applications>Office>**Open Office Writer**. then when you save choose save as Microsoft Word document. This programme can read and write in .doc format.
HELLO guys i'm not telling the word or open office editor.. i meant "text to speech" if we write something it should read in some voices..... lik "microsoft sam" which will be control panel in windows..

---

### Post by aysiu on 2010-09-01
> **munna.cheyur said:**
> HELLO guys i'm not telling the word or open office editor.. i meant "text to speech" if we write something it should read in some voices..... lik "microsoft sam" which will be control panel in windows.. Go to Applications > Ubuntu Software Center. Then type *speech* in the search filter to find text-to-speech programs. Pick the one you like.

---

### Post by marl30 on 2010-09-01
> **munna.cheyur said:**
> HELLO guys i'm not telling the word or open office editor.. i meant "text to speech" if we write something it should read in some voices..... lik "microsoft sam" which will be control panel in windows..

Just to add to this thread. Typing tts (short for text to speech) in Synaptic Package Manager brings up some additional tts software that are not in the Software Center. Look for one called Gespeaker, which is the simples one to use. 

Or you can do like me and install better voices with Windows versions running on Wine. Check this link on how to install them through Wine: [http://www.nextup.com/phpBB2/viewtopic.php?t=3349](http://www.nextup.com/phpBB2/viewtopic.php?t=3349)

---

### Post by inameiname on 2010-09-01
What about eSpeak? It comes preinstalled, and runs from the terminal. It is a basic one, with a normal synthesized voice, but it works just fine. Here is the help readout of it:

```

eSpeak text-to-speech: 1.43.03  13.Mar.10

speak [options] ["<words>"]

-f <text file>   Text file to speak
--stdin    Read text input from stdin instead of a file

If neither -f nor --stdin, then <words> are spoken, or if none then text
is spoken from stdin, each line separately.

-a <integer>
       Amplitude, 0 to 200, default is 100
-g <integer>
       Word gap. Pause between words, units of 10mS at the default speed
-l <integer>
       Line length. If not zero (which is the default), consider
       lines less than this length as end-of-clause
-p <integer>
       Pitch adjustment, 0 to 99, default is 50
-s <integer>
       Speed in words per minute, 80 to 390, default is 170
-v <voice name>
       Use voice file of this name from espeak-data/voices
-w <wave file name>
       Write output to this WAV file, rather than speaking it directly
-b       Input text encoding, 1=UTF8, 2=8 bit, 4=16 bit 
-m       Interpret SSML markup, and ignore other < > tags
-q       Quiet, don't produce any speech (may be useful with -x)
-x       Write phoneme mnemonics to stdout
-X       Write phonemes mnemonics and translation trace to stdout
-z       No final sentence pause at the end of the text
--stdout   Write speech output to stdout
--compile=<voice name>
       Compile the pronunciation rules and dictionary in the current
       directory. <voice name> specifies the language
--path="<path>"
       Specifies the directory containing the espeak-data directory
--phonout="<filename>"
       Write output from -x -X commands, and mbrola phoneme data, to this file
--punct="<characters>"
       Speak the names of punctuation characters during speaking.  If
       =<characters> is omitted, all punctuation is spoken.
--split="<minutes>"
       Starts a new WAV file every <minutes>.  Used with -w
--voices=<language>
       List the available voices for the specified language.
       If <language> is omitted, then list all voices.
-k <integer>
       Indicate capital letters with: 1=sound, 2=the word "capitals",
       higher values indicate a pitch increase (try -k20).

```I know that in place of 'words' in a terminal command, you can have it read a document.

There is also an eSpeak frontend if you'd like:

sudo apt-get install gespeaker

And to install it and a much better voice, male and female:

sudo apt-get install gespeaker mbrola mbrola-us1 mbrola-us2

---

