---
title: "Xsane is driving me Insane"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by js@lloyd on 2009-03-31
If I can just get my HP Scanjet 8250 to run, then I really have no need to use XP on this machine anymore.  However, I've had no luck.  I've removed/re-installed.  It recognizes the scanner when it launches, and I select my scanner.  Here's what typically happens. I make my selections (scan to a PDF and save to my documents), then click scan. The 1st attempt usually crashes the computer and restarts.  After that, it just closes out XSane after I click scan.  The scanner makes a noise as if it's going to start the scan, then nothing.  I sure would appreciate any help/suggestions on this one.

Thanks,

JSS

---

### Post by wolfen69 on 2009-03-31
remove the hplip you have, and install the latest one. get it [here]("http://hplipopensource.com/hplip-web/index.html"). put it in your home folder and do
```
sh hplip-3.9.2.run
```
follow the prompts. i suggest selecting automatic install.

---

### Post by js@lloyd on 2009-03-31
> **wolfen69 said:**
> remove the hplip you have, and install the latest one. get it [here]("http://hplipopensource.com/hplip-web/index.html"). put it in your home folder and do
```
sh hplip-3.9.2.run
```
follow the prompts. i suggest selecting automatic install.

---Scratch the response below. I figured it out.  Thanks.---

Thanks.  I attempted to do this before, but I was able to run it. Being that I'm new, I'm not familiar with how to saving it to my "home" folder.  Any suggestions?
THanks,
JS

---

### Post by js@lloyd on 2009-03-31
Now, I have new issues.  I was installing the hp update, but I can't finalize it.  It doesn't see the scanner, even though XSane does see it.  Any help?
[IMG]http://i728.photobucket.com/albums/ww284/jsinlloyd/xsanehp-1-1.png[/IMG]

---

### Post by sgosnell on 2009-03-31
Do you have xsane open while doing the update?  Or are you opening it after the scan fails?  If it's already open and has control of the scanner, that might be the problem.  Other than that, I dunno.  My HP works flawlessly in Ubuntu, but in XP the scanner won't work at all.  I can't even install the HP software in XP, even after hours on the phone to India and a new CD.  I haven't booted Windows on the small HDD in months.  I would get rid of it, but I really have no other use for the HDD.

---

### Post by js@lloyd on 2009-03-31
> **sgosnell said:**
> Do you have xsane open while doing the update?  Or are you opening it after the scan fails?  If it's already open and has control of the scanner, that might be the problem.  Other than that, I dunno.  My HP works flawlessly in Ubuntu, but in XP the scanner won't work at all.  I can't even install the HP software in XP, even after hours on the phone to India and a new CD.  I haven't booted Windows on the small HDD in months.  I would get rid of it, but I really have no other use for the HDD.

No, I didn't have it open while installing.  I opened it after to see if Xsane list the Scanner as an option. This is why I can't figure out why it won't recognize it on the install.

---

### Post by halitech on 2009-03-31
never mind, missed that Xsane is seeing it now

---

### Post by js@lloyd on 2009-03-31
Hopefully, I can get this resolved tomorrow morning. I'd love to rid my need of XP.  Perhaps I should remove everything and start all over?  Other suggestions/advice is appreciated.
JS

---

### Post by rockin_goliath on 2009-03-31
Which version of Ubuntu are you running? I am running 8.10 and also have an HP scanner, and I have never had to do the things described here. I just plug in my scanner and it works.
With that said, I don't use Xsane myself, because, well, I don't like it. Try installing gscan2pdf (Applications - Add/Remove) and give that a go. After you install it, restart the computer and just open gscan2pdf, so you can be sure no running processes are conflicting with the access to the scanner.

---

### Post by js@lloyd on 2009-04-01
> **rockin_goliath said:**
> Which version of Ubuntu are you running? I am running 8.10 and also have an HP scanner, and I have never had to do the things described here. I just plug in my scanner and it works.
With that said, I don't use Xsane myself, because, well, I don't like it. Try installing gscan2pdf (Applications - Add/Remove) and give that a go. After you install it, restart the computer and just open gscan2pdf, so you can be sure no running processes are conflicting with the access to the scanner.

I'm running 8.10.  I tried installing gscan, but am getting an error with this too.  Here's a screen shot.

[IMG]http://i728.photobucket.com/albums/ww284/jsinlloyd/gscan.png[/IMG]

---

### Post by rockin_goliath on 2009-04-02
Ouch. Segmentation fault?! You've stumped me.
Bump.

---

### Post by ecowan on 2009-05-27
Me too.
I have an HP 8250. I've tried kooka and xsane, on Kubuntu 8.04 and kubuntu 8.10 laptop. 

Both recognize the scanner. But when I hit Acquire Preview or Scan, after a long pause (I'm guessing it's been waiting for the lamp to warm up.) X windows restarts.

I just applied this morning's updates to 8.10. Now when I try xsane, at least the scan light carridge slides across.
I ran xsane from a terminal window, both as me and as sudo. Either way it ends with a 'segmentation fault' message.

I have no such trouble with my Epson CX3810 scanner.

This problem seems to have generated several threads over some time.

Is anyone investigating this? Can I help with some diagnostic material?

Thanks. - Erny

---

### Post by durand on 2009-05-27
Have you tried the gnome scanner? I think it uses the same backend as xsane but it may work better for you..
```
sudo aptitude install flegita
```

---

### Post by ecowan on 2009-06-02
I tried flegita, with the same result, almost. This time x windows crashes but it does not restart cleanly, but with a jitterly display, which can be rectified by picking 'Restart x-windows' from the logon screen.
Thanks for trying to help. - Erny

---

### Post by ecowan on 2009-06-03
I've collected a little more diagnostic material, in the hope that someone will find it helpful.
I ran flegita inside a terminal session:
```
(flegita:7621): GnomeScan-DEBUG: Reloading option br-x
(flegita:7621): GnomeScan-DEBUG:  flags = { range }
(flegita:7621): GnomeScan-DEBUG:  type  = gdouble
(flegita:7621): GnomeScan-DEBUG:  value = 215.899994
(flegita:7621): GnomeScan-DEBUG: Option depth is unknown for device avision:libu                     sb:004:002. Skipping.
Terminated

```
With kooka I get:```
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
Terminated

```
With gscan2pdf I get:```
Use of uninitialized value in subroutine entry at /usr/bin/gscan2pdf line 4680.
Use of uninitialized value in subroutine entry at /usr/bin/gscan2pdf line 4680.
Terminated

```
Does anyone find this helpful? - Erny

---

### Post by ecowan on 2009-06-03
I also ran gscan2pdf --debug:```
gscan2pdf 0.9.21
Using en_CA.UTF-8 locale
Gtk2-Perl version 1.161
Built for 2.12.0
Running with 2.12.9
$VAR1 = {
          'ocr panel' => '572',
          'frontend' => 'scanimage',
          'Paper' => {
                       'US Legal' => {
                                       'l' => '0',
                                       'y' => '356',
                                       'x' => '216',
                                       't' => '0'
                                     },
                       'US Letter' => {
                                        'l' => '0',
                                        'y' => '279',
                                        'x' => '216',
                                        't' => '0'
                                      },
                       'A4' => {
                                 'l' => '0',
                                 'y' => '297',
                                 'x' => '210',
                                 't' => '0'
                               }
                     },
          'window_maximize' => '1',
          'downsample dpi' => '150',
          'layout' => 'single',
          'cwd' => '/home/erny',
          'window_width' => '1024',
          'threshold tool' => '80',
          'window_x' => '0',
          'window_y' => '0',
          't' => '0',
          'thumb panel' => '128',
          'enable options' => '1',
          'Page range' => 'all',
          'version' => '0.9.21',
          'window_height' => '744',
          'startup warning' => '',
          'l' => '0',
          'Page range default' => 'all',
          'downsample' => '',
          'restore window' => '1'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found xdg-email
Found libtiff
scanimage --formatted-device-list="'%i','%d','%v %m'
" 2>/dev/null
Forked PID 11566
Waiting to reap process at /usr/bin/gscan2pdf line 3523.
Reaped PID -1
'0','avision:libusb:004:002','Hewlett-Packard ScanJet 8200'
scanimage --help --device-name='avision:libusb:004:002'
Forked PID 11576
Waiting to reap process at /usr/bin/gscan2pdf line 4443.
Reaped PID -1
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write PNM image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), and %i (index number)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase number in filename by an amount of #
    --batch-double         increment page number by two for 2sided originals
                           being scanned in a single sided scanner
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size          change default input buffersize
-V, --version              print version information

Options specific to device `avision:libusb:004:002':
  Scan mode:
    --mode Lineart|Dithered|Gray|16bit Gray|Color|16bit Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 50..4800dpi (in steps of 1) [150]
        Sets the resolution of the scanned image.
    --speed 0..4 (in steps of 1) [0]
        Determines the speed at which the scan proceeds.
    --preview[=(yes|no)] [no]
        Request a preview-quality scan.
    --source Normal|ADF Front [Normal]
        Selects the scan source (such as a document-feeder).
  Geometry:
    -l 0..216mm [0]
        Top-left x position of scan area.
    -t 0..355mm [0]
        Top-left y position of scan area.
    -x 0..216mm [216]
        Width of scan-area.
    -y 0..355mm [355]
        Height of scan-area.
    --overscan-top 0..4mm [inactive]
        The top overscan controls the additional area to scan before the paper
        is detected.
    --overscan-bottom 0..4mm [inactive]
        The bottom overscan controls the additional area to scan after the
        paper end was detected.
    --background-lines 0..50pel [inactive]
        The background raster controls the additional background lines to scan
        before the paper is feed thru the scanner.
  Enhancement:
    --brightness -100..100% (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..100% (in steps of 1) [0]
        Controls the contrast of the acquired image.
    --quality-scan[=(yes|no)] [yes]
        Turn on quality scanning (slower but better).
    --quality-cal[=(yes|no)] [yes]
        Do a quality white-calibration
    --gamma-table 0..255,... [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..255,...
        Gamma-correction table for the red band.
    --green-gamma-table 0..255,...
        Gamma-correction table for the green band.
    --blue-gamma-table 0..255,...
        Gamma-correction table for the blue band.
    --frame 0..0 [inactive]
        Selects the number of the frame to scan
    --power-save-time <int> [40]
        Allows control of the scanner's power save timer, dimming or turning
        off the light.
    --nvram-values <string> [Vendor: HP
Model: C9930A
Firmware: 1.03
Manufacturing date: 12336-13123-16980
First scan date: 2056-12344-14080
Flatbed scans: 202048256
Pad scans: 7914
ADF simplex scans: 825110579]
        Allows access obtaining the scanner's NVRAM values as pretty printed
        text.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    avision:libusb:004:002
$VAR1 = {
          'source' => {
                        'tip' => 'Selects the scan source (such as a document-feeder).',
                        'default' => 'Normal',
                        'values' => [
                                      'Normal',
                                      'ADF Front'
                                    ]
                      },
          'gamma-table' => {
                             'tip' => 'Gamma-correction table.  In color mode this option equally affects the red, green, and blue channels simultaneously (i.e., it is an intensity gamma table).',
                             'min' => '0',
                             'max' => '255',
                             'default' => 'inactive'
                           },
          'mode' => {
                      'tip' => 'Selects the scan mode (e.g., lineart, monochrome, or color).',
                      'default' => 'Color',
                      'values' => [
                                    'Lineart',
                                    'Dithered',
                                    'Gray',
                                    '16bit Gray',
                                    'Color',
                                    '16bit Color'
                                  ]
                    },
          'contrast' => {
                          'tip' => 'Controls the contrast of the acquired image.',
                          'step' => '1',
                          'min' => '-100',
                          'max' => '100',
                          'default' => '0'
                        },
          'quality-cal' => {
                             'tip' => 'Do a quality white-calibration',
                             'default' => 'yes',
                             'values' => [
                                           'yes',
                                           'no'
                                         ]
                           },
          'frame' => {
                       'tip' => 'Selects the number of the frame to scan',
                       'min' => '0',
                       'max' => '0',
                       'default' => 'inactive'
                     },
          'overscan-bottom' => {
                                 'tip' => 'The bottom overscan controls the additional area to scan after the paper end was detected.',
                                 'min' => '0',
                                 'max' => '4',
                                 'default' => 'inactive'
                               },
          'brightness' => {
                            'tip' => 'Controls the brightness of the acquired image.',
                            'step' => '1',
                            'min' => '-100',
                            'max' => '100',
                            'default' => '0'
                          },
          'preview' => {
                         'tip' => 'Request a preview-quality scan.',
                         'default' => 'no',
                         'values' => [
                                       'yes',
                                       'no'
                                     ]
                       },
          'speed' => {
                       'tip' => 'Determines the speed at which the scan proceeds.',
                       'step' => '1',
                       'min' => '0',
                       'max' => '4',
                       'default' => '0'
                     },
          'overscan-top' => {
                              'tip' => 'The top overscan controls the additional area to scan before the paper is detected.',
                              'min' => '0',
                              'max' => '4',
                              'default' => 'inactive'
                            },
          'resolution' => {
                            'tip' => 'Sets the resolution of the scanned image.',
                            'step' => '1',
                            'min' => '50',
                            'max' => '4800',
                            'default' => '150'
                          },
          'power-save-time' => {
                                 'tip' => 'Allows control of the scanner\'s power save timer, dimming or turning off the light.',
                                 'default' => '40',
                                 'values' => [
                                               '<int>'
                                             ]
                               },
          'background-lines' => {
                                  'tip' => 'The background raster controls the additional background lines to scan before the paper is feed thru the scanner.',
                                  'min' => '0',
                                  'max' => '50',
                                  'default' => 'inactive'
                                },
          'quality-scan' => {
                              'tip' => 'Turn on quality scanning (slower but better).',
                              'default' => 'yes',
                              'values' => [
                                            'yes',
                                            'no'
                                          ]
                            }
        };
Use of uninitialized value in subroutine entry at /usr/bin/gscan2pdf line 4680.
Use of uninitialized value in subroutine entry at /usr/bin/gscan2pdf line 4680.
$VAR1 = [];
$VAR1 = {
          'source' => 'Normal',
          'mode' => 'Color',
          'contrast' => '0',
          'x' => '210',
          'l' => '0',
          'y' => '297',
          'brightness' => '0',
          'speed' => '0',
          'resolution' => '150',
          't' => '0'
        };
scanimage --device-name='avision:libusb:004:002' --mode='Color' --source='Normal' --contrast='0' -x 210 -l 0 -y 297 --brightness='0' --speed='0' --resolution='150' -t 0 --batch --progress --batch-count=1
Forked PID 11590
Scanning 1 pages, incrementing by 1, numbering from 1
Scanning page 1
Terminated

```

---

### Post by ecowan on 2009-06-03
Since four different 'front-end' scanner programs are all crashing x-windows, and sane-avision seems to be the common back-end, i did a little more digging. I found a suggestion on [www.sane-project.org/man/sane-avision.5.html](www.sane-project.org/man/sane-avision.5.html). So I tried ```
erny@mistry:~$ export SANE_DEBUG_AVISION=7
erny@mistry:~$ kooka
[sanei_debug] Setting debug level of avision to 7.
[avision] sane_init:(Version: 1.0 Build: 264)
[avision] sane_init: parsing config line ""
[avision] sane_init: config file line 1: ignoring empty line
[avision] sane_init: parsing config line "# This are the possible options. Normally any scanner"
[avision] sane_init: config file line 2: ignoring comment line
[avision] sane_init: parsing config line "# should work just fine without them - and they are only"
[avision] sane_init: config file line 3: ignoring comment line
[avision] sane_init: parsing config line "# needed for test and debugging. So if you experience problems"
[avision] sane_init: config file line 4: ignoring comment line
[avision] sane_init: parsing config line "# and you solve them with enabling options here, please notify"
[avision] sane_init: config file line 5: ignoring comment line
[avision] sane_init: parsing config line "# the SANE/Avision maintainer: Rene Rebe <rene@exactcode.de>"
[avision] sane_init: config file line 6: ignoring comment line
[avision] sane_init: parsing config line ""
[avision] sane_init: config file line 7: ignoring empty line
[avision] sane_init: parsing config line "#option disable-gamma-table"
[avision] sane_init: config file line 8: ignoring comment line
[avision] sane_init: parsing config line "#option disable-calibration"
[avision] sane_init: config file line 9: ignoring comment line
[avision] sane_init: parsing config line "#option force-a4"
[avision] sane_init: config file line 10: ignoring comment line
[avision] sane_init: parsing config line ""
[avision] sane_init: config file line 11: ignoring empty line
[avision] sane_init: parsing config line "#scsi AVISION"
[avision] sane_init: config file line 12: ignoring comment line
[avision] sane_init: parsing config line "#scsi FCPA"
[avision] sane_init: config file line 13: ignoring comment line
[avision] sane_init: parsing config line "#scsi MINOLTA"
[avision] sane_init: config file line 14: ignoring comment line
[avision] sane_init: parsing config line "#scsi MITSBISH MCA-S600C"
[avision] sane_init: config file line 15: ignoring comment line
[avision] sane_init: parsing config line "#scsi MITSBISH MCA-SS600"
[avision] sane_init: config file line 16: ignoring comment line
[avision] sane_init: parsing config line "#scsi HP"
[avision] sane_init: config file line 17: ignoring comment line
[avision] sane_init: parsing config line "#scsi hp"
[avision] sane_init: config file line 18: ignoring comment line
[avision] sane_init: parsing config line ""
[avision] sane_init: config file line 19: ignoring empty line
[avision] sane_init: parsing config line "#scsi /dev/scanner"
[avision] sane_init: config file line 20: ignoring comment line
[avision] sane_init: parsing config line "# usb libusb:002:003"
[avision] sane_init: config file line 21: ignoring comment line
[avision] sane_init: parsing config line "# usb 0x03f0 0x0701"
[avision] sane_init: config file line 22: ignoring comment line
[avision] sane_init: parsing config line "# 20090602 ecowan added"
[avision] sane_init: config file line 23: ignoring comment line
[avision] sane_init: parsing config line "usb 0x03f0:0x0b01"
[avision] sane_init: config file line 24: trying to attach USB:`usb 0x03f0:0x0b01'
[avision] sane_init: parsing config line ""
[avision] sane_init: config file line 25: ignoring empty line
[avision] sane_init: Trying to find USB device 638 a27 ...
[avision] sane_init: Trying to find USB device 638 a3c ...
[avision] sane_init: Trying to find USB device 638 a33 ...
[avision] sane_init: Trying to find USB device 638 a93 ...
[avision] sane_init: Trying to find USB device 638 a24 ...
[avision] sane_init: Trying to find USB device 638 a25 ...
[avision] sane_init: Trying to find USB device 638 a3a ...
[avision] sane_init: Trying to find USB device 638 a3a ...
[avision] sane_init: Trying to find USB device 638 a23 ...
[avision] sane_init: Trying to find USB device 638 a2a ...
[avision] sane_init: Trying to find USB device 638 a19 ...
[avision] sane_init: Trying to find USB device 638 a5e ...
[avision] sane_init: Trying to find USB device 638 a41 ...
[avision] sane_init: Trying to find USB device 638 a16 ...
[avision] sane_init: Trying to find USB device 638 a13 ...
[avision] sane_init: Trying to find USB device 638 a18 ...
[avision] sane_init: Trying to find USB device 638 a66 ...
[avision] sane_init: Trying to find USB device 638 a82 ...
[avision] sane_init: Trying to find USB device 638 a84 ...
[avision] sane_init: Trying to find USB device 638 a4d ...
[avision] sane_init: Trying to find USB device 638 a40 ...
[avision] sane_init: Trying to find USB device 638 a68 ...
[avision] sane_init: Trying to find USB device 638 a61 ...
[avision] sane_init: Trying to find USB device 638 aa1 ...
[avision] sane_init: Trying to find USB device 638 a45 ...
[avision] sane_init: Trying to find USB device 3f0 701 ...
[avision] sane_init: Trying to find USB device 3f0 701 ...
[avision] sane_init: Trying to find USB device 3f0 801 ...
[avision] sane_init: Trying to find USB device 3f0 b01 ...
[avision] attach:
[avision] attach: opening libusb:004:004
[avision] inquiry: length: 96
[avision] inquiry: inquiring ...
[avision] filling command to have a length of 10, was: 6
[avision] Timeouts: write: 30000, read: 15000, status: 15000
[avision] avision_usb_status: timeout 15000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] attach: Inquiry gives mfg=HP, model=C9930A, product revision=1.03.
[avision] attach: Checking model: 0
[avision] attach: Checking model: 1
[avision] attach: Checking model: 2
[avision] attach: Checking model: 3
[avision] attach: Checking model: 4
[avision] attach: Checking model: 5
[avision] attach: Checking model: 6
[avision] attach: Checking model: 7
[avision] attach: Checking model: 8
[avision] attach: Checking model: 9
[avision] attach: Checking model: 10
[avision] attach: Checking model: 11
[avision] attach: Checking model: 12
[avision] attach: Checking model: 13
[avision] attach: Checking model: 14
[avision] attach: Checking model: 15
[avision] attach: Checking model: 16
[avision] attach: Checking model: 17
[avision] attach: Checking model: 18
[avision] attach: Checking model: 19
[avision] attach: Checking model: 20
[avision] attach: Checking model: 21
[avision] attach: Checking model: 22
[avision] attach: Checking model: 23
[avision] attach: Checking model: 24
[avision] attach: Checking model: 25
[avision] attach: Checking model: 26
[avision] attach: Checking model: 27
[avision] attach: Checking model: 28
[avision] attach: Checking model: 29
[avision] attach: Checking model: 30
[avision] attach: Checking model: 31
[avision] attach: Checking model: 32
[avision] attach: Checking model: 33
[avision] attach: Checking model: 34
[avision] attach: Checking model: 35
[avision] attach: Checking model: 36
[avision] attach: Checking model: 37
[avision] attach: Checking model: 38
[avision] attach: Checking model: 39
[avision] attach: Checking model: 40
[avision] attach: Checking model: 41
[avision] attach: Checking model: 42
[avision] attach: Checking model: 43
[avision] attach: Checking model: 44
[avision] attach: Checking model: 45
[avision] attach: Checking model: 46
[avision] attach: Checking model: 47
[avision] attach: Checking model: 48
[avision] attach: Checking model: 49
[avision] attach: Checking model: 50
[avision] attach: Checking model: 51
[avision] attach: Checking model: 52
[avision] attach: Checking model: 53
[avision] attach: Checking model: 54
[avision] attach: Checking model: 55
[avision] attach: Checking model: 56
[avision] attach: Checking model: 57
[avision] attach: Checking model: 58
[avision] attach: Checking model: 59
[avision] attach: Scanner matched entry: 59: "HP", "C9930A", 0x3f0, 0xb01
[avision] inquiry: length: 96
[avision] inquiry: inquiring ...
[avision] filling command to have a length of 10, was: 6
[avision] Timeouts: write: 30000, read: 15000, status: 15000
[avision] avision_usb_status: timeout 15000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] inquiry: length: 136
[avision] inquiry: inquiring ...
[avision] filling command to have a length of 10, was: 6
[avision] Timeouts: write: 30000, read: 15000, status: 15000
[avision] avision_usb_status: timeout 15000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] attach: raw data:
[avision]   [0] 00000110b   6o   6d  6x
[avision]   [1] 00000000b   0o   0d  0x
[avision]   [2] 00000010b   2o   2d  2x
[avision]   [3] 00000010b   2o   2d  2x
[avision]   [4] 01011011b 133o  91d 5bx
[avision]   [5] 00000000b   0o   0d  0x
[avision]   [6] 00000000b   0o   0d  0x
[avision]   [7] 00000000b   0o   0d  0x
[avision]   [8] 01001000b 110o  72d 48x
[avision]   [9] 01010000b 120o  80d 50x
[avision]   [10] 00100000b  40o  32d 20x
[avision]   [11] 00100000b  40o  32d 20x
[avision]   [12] 00100000b  40o  32d 20x
[avision]   [13] 00100000b  40o  32d 20x
[avision]   [14] 00100000b  40o  32d 20x
[avision]   [15] 00100000b  40o  32d 20x
[avision]   [16] 01000011b 103o  67d 43x
[avision]   [17] 00111001b  71o  57d 39x
[avision]   [18] 00111001b  71o  57d 39x
[avision]   [19] 00110011b  63o  51d 33x
[avision]   [20] 00110000b  60o  48d 30x
[avision]   [21] 01000001b 101o  65d 41x
[avision]   [22] 00100000b  40o  32d 20x
[avision]   [23] 00100000b  40o  32d 20x
[avision]   [24] 00100000b  40o  32d 20x
[avision]   [25] 00100000b  40o  32d 20x
[avision]   [26] 00100000b  40o  32d 20x
[avision]   [27] 00100000b  40o  32d 20x
[avision]   [28] 00100000b  40o  32d 20x
[avision]   [29] 00100000b  40o  32d 20x
[avision]   [30] 00100000b  40o  32d 20x
[avision]   [31] 00100000b  40o  32d 20x
[avision]   [32] 00110000b  60o  48d 30x
[avision]   [33] 00101110b  56o  46d 2ex
[avision]   [34] 00110000b  60o  48d 30x
[avision]   [35] 00110001b  61o  49d 31x
[avision]   [36] 10100001b 241o 161d a1x
[avision]   [37] 00110000b  60o  48d 30x
[avision]   [38] 00110000b  60o  48d 30x
[avision]   [39] 01100111b 147o 103d 67x
[avision]   [40] 00010010b  22o  18d 12x
[avision]   [41] 11000000b 300o 192d c0x
[avision]   [42] 00010010b  22o  18d 12x
[avision]   [43] 11000000b 300o 192d c0x
[avision]   [44] 00010010b  22o  18d 12x
[avision]   [45] 11000000b 300o 192d c0x
[avision]   [46] 00010010b  22o  18d 12x
[avision]   [47] 11000000b 300o 192d c0x
[avision]   [48] 00000000b   0o   0d  0x
[avision]   [49] 00000000b   0o   0d  0x
[avision]   [50] 11011001b 331o 217d d9x
[avision]   [51] 10010110b 226o 150d 96x
[avision]   [52] 11010011b 323o 211d d3x
[avision]   [53] 01000000b 100o  64d 40x
[avision]   [54] 00001000b  10o   8d  8x
[avision]   [55] 00001000b  10o   8d  8x
[avision]   [56] 00000010b   2o   2d  2x
[avision]   [57] 00001000b  10o   8d  8x
[avision]   [58] 00001000b  10o   8d  8x
[avision]   [59] 00001000b  10o   8d  8x
[avision]   [60] 11000000b 300o 192d c0x
[avision]   [61] 11010010b 322o 210d d2x
[avision]   [62] 00100000b  40o  32d 20x
[avision]   [63] 00000101b   5o   5d  5x
[avision]   [64] 00000001b   1o   1d  1x
[avision]   [65] 00000001b   1o   1d  1x
[avision]   [66] 00000010b   2o   2d  2x
[avision]   [67] 00000011b   3o   3d  3x
[avision]   [68] 00000100b   4o   4d  4x
[avision]   [69] 00000101b   5o   5d  5x
[avision]   [70] 00000000b   0o   0d  0x
[avision]   [71] 00000000b   0o   0d  0x
[avision]   [72] 00000000b   0o   0d  0x
[avision]   [73] 00000000b   0o   0d  0x
[avision]   [74] 00000000b   0o   0d  0x
[avision]   [75] 00001111b  17o  15d  fx
[avision]   [76] 00000000b   0o   0d  0x
[avision]   [77] 00000010b   2o   2d  2x
[avision]   [78] 00001000b  10o   8d  8x
[avision]   [79] 00000111b   7o   7d  7x
[avision]   [80] 00111110b  76o  62d 3ex
[avision]   [81] 00001001b  11o   9d  9x
[avision]   [82] 11111000b 370o 248d f8x
[avision]   [83] 00010000b  20o  16d 10x
[avision]   [84] 01101000b 150o 104d 68x
[avision]   [85] 00001001b  11o   9d  9x
[avision]   [86] 11111000b 370o 248d f8x
[avision]   [87] 00010000b  20o  16d 10x
[avision]   [88] 01101000b 150o 104d 68x
[avision]   [89] 00010010b  22o  18d 12x
[avision]   [90] 11000000b 300o 192d c0x
[avision]   [91] 00000110b   6o   6d  6x
[avision]   [92] 00000111b   7o   7d  7x
[avision]   [93] 10001000b 210o 136d 88x
[avision]   [94] 00000000b   0o   0d  0x
[avision]   [95] 00000000b   0o   0d  0x
[avision]   [96] 01010000b 120o  80d 50x
[avision]   [97] 01100001b 141o  97d 61x
[avision]   [98] 01100011b 143o  99d 63x
[avision]   [99] 01101011b 153o 107d 6bx
[avision]   [100] 01100001b 141o  97d 61x
[avision]   [101] 01110010b 162o 114d 72x
[avision]   [102] 01100100b 144o 100d 64x
[avision]   [103] 00000000b   0o   0d  0x
[avision]   [104] 00000000b   0o   0d  0x
[avision]   [105] 00000000b   0o   0d  0x
[avision]   [106] 00000000b   0o   0d  0x
[avision]   [107] 00000000b   0o   0d  0x
[avision]   [108] 00000000b   0o   0d  0x
[avision]   [109] 00000000b   0o   0d  0x
[avision]   [110] 00000000b   0o   0d  0x
[avision]   [111] 00000000b   0o   0d  0x
[avision]   [112] 00000000b   0o   0d  0x
[avision]   [113] 00001111b  17o  15d  fx
[avision]   [114] 01101000b 150o 104d 68x
[avision]   [115] 01110000b 160o 112d 70x
[avision]   [116] 00100000b  40o  32d 20x
[avision]   [117] 01110011b 163o 115d 73x
[avision]   [118] 01100011b 143o  99d 63x
[avision]   [119] 01100001b 141o  97d 61x
[avision]   [120] 01101110b 156o 110d 6ex
[avision]   [121] 01101010b 152o 106d 6ax
[avision]   [122] 01100101b 145o 101d 65x
[avision]   [123] 01110100b 164o 116d 74x
[avision]   [124] 00100000b  40o  32d 20x
[avision]   [125] 00111000b  70o  56d 38x
[avision]   [126] 00110010b  62o  50d 32x
[avision]   [127] 00110000b  60o  48d 30x
[avision]   [128] 00000000b   0o   0d  0x
[avision]   [129] 00000000b   0o   0d  0x
[avision]   [130] 00000000b   0o   0d  0x
[avision]   [131] 00000000b   0o   0d  0x
[avision]   [132] 00000000b   0o   0d  0x
[avision]   [133] 00000000b   0o   0d  0x
[avision]   [134] 00000000b   0o   0d  0x
[avision]   [135] 00000000b   0o   0d  0x
[avision] attach: [8-15]  Vendor id.:      'HP      '
[avision] attach: [16-31] Product id.:     'C9930A          '
[avision] attach: [32-35] Product rev.:    '0.01'
[avision] attach: [36]    Bitfield: ADF 3-pass color BGR color plane
[avision] attach: [37]    Optical res.:    4800 dpi
[avision] attach: [38]    Maximum res.:    4800 dpi
[avision] attach: [39]    Bitfield1: Q_SCAN EXTENDED_RES NEW_PROTOCOL AVISION
[avision] attach: [40-41] X res. in gray:  4800 dpi
[avision] attach: [42-43] Y res. in gray:  4800 dpi
[avision] attach: [44-45] X res. in color: 4800 dpi
[avision] attach: [46-47] Y res. in color: 4800 dpi
[avision] attach: [48-49] USB max read:    0
[avision] attach: [50]    ESA1: LIGHT_CONTROL BUTTON_CONTROL SW_CALIB NEED_SW_GAMMA XYRES_DIFFERENT
[avision] attach: [51]    ESA2: EXPOSURE_CTRL SUPPORTS_QUALITY_SPEED_CAL HAS_PUSH_BUTTON NEW_CAL_METHOD_3x3_MATRIX_(NO_GAMMA_TABLE)
[avision] attach: [52]    ESA3: GRAY_WHITE SUPPORTS_GAIN_CONTROL 3x3COL_TABLE POWER_SAVING_TIMER NVM_DATA_REC
[avision] attach: [53]    line difference (software color pack): 64
[avision] attach: [54]    color mode pixel boundary: 8
[avision] attach: [55]    gray mode pixel boundary: 8
[avision] attach: [56]    4bit gray mode pixel boundary: 2
[avision] attach: [57]    lineart mode pixel boundary: 8
[avision] attach: [58]    halftone mode pixel boundary: 8
[avision] attach: [59]    error-diffusion mode pixel boundary: 8
[avision] attach: [60]    channels per pixel: 1 3
[avision] attach: [61]    bits per channel: 1 4 8 16
[avision] attach: [62]    scanner type: Flatbed (ADF)
[avision] attach: [75-76] Max shading target : f00
[avision] attach: [77-78] Max X of transparency: 520 dots * base_dpi
[avision] attach: [79-80] Max Y of transparency: 1854 dots * base_dpi
[avision] attach: [81-82] Max X of flatbed:      2552 dots * base_dpi
[avision] attach: [83-84] Max Y of flatbed:      4200 dots * base_dpi
[avision] attach: [85-86] Max X of ADF:          2552 dots * base_dpi
[avision] attach: [87-88] Max Y of ADF:          4200 dots * base_dpi
[avision] attach: [89-90] Res. in Ex. mode:      4800 dpi
[avision] attach: [91]    ASIC:     6
[avision] attach: [92]    Buttons:  7
[avision] attach: [93]    ESA4: SUPPORTS_ACCESSORIES_DETECT SUPPORTS_ASIC_UPDATE
[avision] attach: [94]    ESA5:
[avision] attach: [95]    ESA6:
[avision] attach: [128]    ESA7:
[avision] attach: [129]    YCbCr:
[avision] attach: optical resolution set to: 4800 dpi
[avision] attach: max resolution set to: 4800 dpi
[avision] attach: max channels per pixel: 3, max bits per channel: 16
[avision] attach: x/y-range for mode 0 is valid!
[avision] attach: Mode 0 range is now: 216.169333 x 355.600000 mm.
[avision] attach: x/y-range for mode 1 is valid!
[avision] attach: Mode 1 range is now: 44.126667 x 156.972000 mm.
[avision] attach: x/y-range for mode 2 is valid!
[avision] attach: Mode 2 range is now: 216.169333 x 355.600000 mm.
[avision] sane_init: Trying to find USB device 3f0 3905 ...
[avision] sane_init: Trying to find USB device 3f0 3805 ...
[avision] sane_init: Trying to find USB device 638 26a ...
[avision] sane_init: Trying to find USB device 686 4004 ...
[avision] sane_init: Trying to find USB device 686 400d ...
[avision] sane_init: Trying to find USB device 686 400e ...
[avision] sane_init: Trying to find USB device 638 a15 ...
[avision] sane_init: Trying to find USB device 638 a16 ...
[avision] sane_init: Trying to find USB device 4c5 1029 ...
[avision] sane_init: Trying to find USB device 40a 6001 ...
[avision] sane_init: Trying to find USB device 40a 6002 ...
[avision] sane_init: Trying to find USB device 40a 6003 ...
[avision] sane_init: Trying to find USB device 40a 6003 ...
[avision] sane_init: Trying to find USB device 40a 6004 ...
[avision] sane_init: Trying to find USB device 40a 6004 ...
[avision] sane_init: Trying to find USB device 40a 6005 ...
[avision] sane_init: Trying to find USB device 638 268 ...
[avision] sane_init: Trying to find USB device 4a7 477 ...
[avision] sane_init: Trying to find USB device 4a7 448 ...
[avision] sane_init: Trying to find USB device 4a7 449 ...
[avision] sane_init: Trying to find USB device 4a7 44c ...
[avision] sane_init: Trying to find USB device 4a7 475 ...
[avision] sane_init: Trying to find USB device 4a7 447 ...
[avision] sane_init: Trying to find USB device 4a7 498 ...
[avision] sane_init: Trying to find USB device 4a7 478 ...
[avision] sane_init: Trying to find USB device 4a7 424 ...
[avision] sane_init: Trying to find USB device 4a7 47a ...
[avision] sane_init: Trying to find USB device 4a7 47b ...
[avision] sane_init: Trying to find USB device 4a7 493 ...
[avision] sane_init: Trying to find USB device 4a7 497 ...
[avision] sane_init: Trying to find USB device 4a7 48f ...
[avision] sane_init: Trying to find USB device 4a7 498 ...
[avision] sane_init: Trying to find USB device 4a7 499 ...
[avision] sane_init: Trying to find USB device 638 a16 ...
[avision] sane_init: Trying to find USB device 482 335 ...
[avision] sane_get_devices:
[avision] sane_open:
[avision] attach:
[avision] sane_open: using open_extended
[avision] sane_open: got 1048576 scsi_max_request_size
[avision] inquiry: length: 96
[avision] inquiry: inquiring ...
[avision] filling command to have a length of 10, was: 6
[avision] Timeouts: write: 30000, read: 15000, status: 15000
[avision] avision_usb_status: timeout 15000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] wait_ready: sending TEST_UNIT_READY
[avision] filling command to have a length of 10, was: 6
[avision] Timeouts: write: 30000, read: 15000, status: 15000
[avision] avision_usb_status: timeout 15000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] get_accessories_info
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] get_accessories_info: raw data:
[avision]   [0] 00000000b   0o   0d  0x
[avision]   [1] 00000000b   0o   0d  0x
[avision]   [2] 00000001b   1o   1d  1x
[avision]   [3] 00000000b   0o   0d  0x
[avision]   [4] 00000000b   0o   0d  0x
[avision]   [5] 00000000b   0o   0d  0x
[avision]   [6] 00000000b   0o   0d  0x
[avision]   [7] 00000000b   0o   0d  0x
[avision] get_accessories_info: [0]  ADF: 0
[avision] get_accessories_info: [1]  Light Box: 0
[avision] get_accessories_info: [2]  ADF model: 1 (Oodles)
[avision] add_color_mode: 0 Lineart
[avision] add_color_mode: 1 Dithered
[avision] add_color_mode: 2 Gray
[avision] add_color_mode: 4 16bit Gray
[avision] add_color_mode: 5 Color
[avision] add_color_mode: 7 16bit Color
[avision] init_options:
[avision] init_options: dpi_range.min set to 50
[avision] max_string_size:
[avision] match_color_mode:
[avision] match_color_mode: found at 4 mode: 5
[avision] max_string_size:
[avision] match_source_mode: "Normal"
[avision] match_source_mode: found at 0 mode: 0
[avision] match_source_mode_dim: 0
[avision] sane_control_option: option=0, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=4, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=5, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=6, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=8, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=9, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=10, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=11, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=12, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=13, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=14, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=16, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=17, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=18, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=19, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=20, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=21, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=22, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=23, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=24, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=25, action=0
[avision] get_power_save_time
[avision] get_nvram_data
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] get_nvram_data: pad scans:             7914
[avision] get_nvram_data: ADF simplex scans:     825110579
[avision] get_nvram_data: ADF duplex scans:      0
[avision] get_nvram_data: flatbed scans:         202048256
[avision] get_nvram_data: flatbed leading edge:  3083
[avision] get_nvram_data: flatbed side edge:     768
[avision] get_nvram_data: ADF leading edge:      0
[avision] get_nvram_data: ADF side edge:         0
[avision] get_nvram_data: ADF rear leading edge: 83
[avision] get_nvram_data: ADF rear side edge:    17230
[avision] get_nvram_data: born month:            13123
[avision] get_nvram_data: born day:              16980
[avision] get_nvram_data: born year:             12336
[avision] get_nvram_data: first scan month:      12344
[avision] get_nvram_data: first scan day:        14080
[avision] get_nvram_data: first scan year:       2056
[avision] get_nvram_data: vert. magnification:   2048
[avision] get_nvram_data: horiz. magnification:  4
[avision] get_nvram_data: CCD type:              2
[avision] get_nvram_data: scan speed:            0
[avision] get_nvram_data: serial:                ''
[avision] get_nvram_data: power saving time:     40
[avision] get_nvram_data: auto feed:             0
[avision] get_nvram_data: roller count:          301996800
[avision] get_nvram_data: multifeed count:       117440515
[avision] get_nvram_data: jam count:             -267714290
[avision] get_nvram_data: identify info:         ''
[avision] get_nvram_data: formal_name:           'd'
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=26, action=0
[avision] get_button_status:
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] get_button_status: raw data
[avision]   [0] 00000000b   0o   0d  0x
[avision]   [1] 00000000b   0o   0d  0x
[avision]   [2] 00000000b   0o   0d  0x
[avision]   [3] 00000000b   0o   0d  0x
[avision]   [4] 00000000b   0o   0d  0x
[avision]   [5] 00000000b   0o   0d  0x
[avision]   [6] 00000000b   0o   0d  0x
[avision]   [7] 00000000b   0o   0d  0x
[avision]   [8] 00000000b   0o   0d  0x
[avision]   [9] 00000000b   0o   0d  0x
[avision]   [10] 00000000b   0o   0d  0x
[avision]   [11] 00000000b   0o   0d  0x
[avision]   [12] 00000000b   0o   0d  0x
[avision]   [13] 00000000b   0o   0d  0x
[avision]   [14] 00000000b   0o   0d  0x
[avision]   [15] 00000000b   0o   0d  0x
[avision] get_button_status: [0]  Button status: 0
[avision] get_button_status: [1]  Button number 0: 0
[avision] get_button_status: [2]  Button number 1: 0
[avision] get_button_status: [3]  Button number 2: 0
[avision] get_button_status: [4]  Button number 3: 0
[avision] get_button_status: [5]  Button number 4: 0
[avision] get_button_status: [7]  Display: 0
[avision] get_button_status: no button pressed
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=27, action=0
[avision] inquiry: length: 96
[avision] inquiry: inquiring ...
[avision] filling command to have a length of 10, was: 6
[avision] Timeouts: write: 30000, read: 15000, status: 15000
[avision] avision_usb_status: timeout 15000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] get_nvram_data
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] get_nvram_data: pad scans:             7914
[avision] get_nvram_data: ADF simplex scans:     825110579
[avision] get_nvram_data: ADF duplex scans:      0
[avision] get_nvram_data: flatbed scans:         202048256
[avision] get_nvram_data: flatbed leading edge:  3083
[avision] get_nvram_data: flatbed side edge:     768
[avision] get_nvram_data: ADF leading edge:      0
[avision] get_nvram_data: ADF side edge:         0
[avision] get_nvram_data: ADF rear leading edge: 83
[avision] get_nvram_data: ADF rear side edge:    17230
[avision] get_nvram_data: born month:            13123
[avision] get_nvram_data: born day:              16980
[avision] get_nvram_data: born year:             12336
[avision] get_nvram_data: first scan month:      12344
[avision] get_nvram_data: first scan day:        14080
[avision] get_nvram_data: first scan year:       2056
[avision] get_nvram_data: vert. magnification:   2048
[avision] get_nvram_data: horiz. magnification:  4
[avision] get_nvram_data: CCD type:              2
[avision] get_nvram_data: scan speed:            0
[avision] get_nvram_data: serial:                ''
[avision] get_nvram_data: power saving time:     40
[avision] get_nvram_data: auto feed:             0
[avision] get_nvram_data: roller count:          301996800
[avision] get_nvram_data: multifeed count:       117440515
[avision] get_nvram_data: jam count:             -267714290
[avision] get_nvram_data: identify info:         ''
[avision] get_nvram_data: formal_name:           'd'
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=10, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=11, action=0
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=5, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=0
libkscan: WARNING: Trying to copy a not healthy option (no name nor desc)
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=4, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=8, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=9, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=2
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=6, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=6, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=4, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=4, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=4, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=4, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=16, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=16, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=16, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=17, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=17, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=17, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=21, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=4, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=16, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=17, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=8, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=9, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=10, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=11, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=8, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=9, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=10, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=11, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=5, action=0
[avision] sane_control_option: option=5, action=2
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=5, action=1
[avision] constrain_value:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=2, action=0
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=0
[avision] sane_get_option_descriptor:
[avision] sane_get_option_descriptor:
[avision] sane_control_option: option=3, action=1
[avision] constrain_value:
[avision] sane_start:
[avision] sane_get_parameters:
[avision] sane_get_parameters: computing parameters
[avision] sane_compute_parameters:
[avision] sane_compute_parameters: boundary 8, gray_mode: 1,
[avision] sane_compute_parameters: tlx: 0.000000, tly: 0.000000, brx: 216.000000, bry: 355.000000
[avision] sane_compute_parameters: hw_xres: 75, hw_yres: 75, line_difference: 0
[avision] sane_compute_parameters: tlx: 0, tly: 0, brx: 637, bry: 1048
[avision] sane_compute_parameters: hw_pixel_per_line: 632, hw_lines: 1048, hw_bytes_per_line: 0
[avision] sane_compute_parameters: xres: 75, yres: 75
[avision] sane_compute_parameters: pixel_per_line: 632, lines: 1048
[avision] sane_compute_parameters: depth: 8, bytes_per_line: 1896
[avision] sane_compute_parameters:
[avision] sane_compute_parameters: boundary 8, gray_mode: 1,
[avision] sane_compute_parameters: tlx: 0.000000, tly: 0.000000, brx: 216.000000, bry: 355.000000
[avision] sane_compute_parameters: hw_xres: 75, hw_yres: 75, line_difference: 0
[avision] sane_compute_parameters: tlx: 0, tly: 0, brx: 637, bry: 1048
[avision] sane_compute_parameters: hw_pixel_per_line: 632, hw_lines: 1048, hw_bytes_per_line: 1896
[avision] sane_compute_parameters: xres: 75, yres: 75
[avision] sane_compute_parameters: pixel_per_line: 632, lines: 1048
[avision] sane_compute_parameters: depth: 8, bytes_per_line: 1896
[avision] wait_4_light: getting light status.
[avision] wait_4_light: read bytes 1
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] wait_4_light: command is 0. Result is on
[avision] set_window:
[avision] set_window: base_dpi_abs: 1200, base_dpi_rel: 1200
[avision] set_window: base paralen: 7
[avision] set_window: final paralen: 20
[avision] set_window: transferlen: 70
[avision] set_window: large data-transfer support (>16bit)!
[avision] set_window: source mode 0 source mode dim 0
[avision] window_data_header:
[avision]   [0] 00000000b   0o   0d  0x
[avision]   [1] 00000000b   0o   0d  0x
[avision]   [2] 00000000b   0o   0d  0x
[avision]   [3] 00000000b   0o   0d  0x
[avision]   [4] 00000000b   0o   0d  0x
[avision]   [5] 00000000b   0o   0d  0x
[avision]   [6] 00000000b   0o   0d  0x
[avision]   [7] 00111110b  76o  62d 3ex
[avision] window_descriptor:
[avision]   [0] 00000000b   0o   0d  0x
[avision]   [1] 00000000b   0o   0d  0x
[avision]   [2] 00000000b   0o   0d  0x
[avision]   [3] 01001011b 113o  75d 4bx
[avision]   [4] 00000000b   0o   0d  0x
[avision]   [5] 01001011b 113o  75d 4bx
[avision]   [6] 00000000b   0o   0d  0x
[avision]   [7] 00000000b   0o   0d  0x
[avision]   [8] 00000000b   0o   0d  0x
[avision]   [9] 00000000b   0o   0d  0x
[avision]   [10] 00000000b   0o   0d  0x
[avision]   [11] 00000000b   0o   0d  0x
[avision]   [12] 00000000b   0o   0d  0x
[avision]   [13] 00000000b   0o   0d  0x
[avision]   [14] 00000000b   0o   0d  0x
[avision]   [15] 00000000b   0o   0d  0x
[avision]   [16] 00100111b  47o  39d 27x
[avision]   [17] 10000001b 201o 129d 81x
[avision]   [18] 00000000b   0o   0d  0x
[avision]   [19] 00000000b   0o   0d  0x
[avision]   [20] 01000001b 101o  65d 41x
[avision]   [21] 10000001b 201o 129d 81x
[avision]   [22] 10000000b 200o 128d 80x
[avision]   [23] 10000000b 200o 128d 80x
[avision]   [24] 10000000b 200o 128d 80x
[avision]   [25] 00000101b   5o   5d  5x
[avision]   [26] 00001000b  10o   8d  8x
[avision]   [27] 00000000b   0o   0d  0x
[avision]   [28] 00000000b   0o   0d  0x
[avision]   [29] 00000011b   3o   3d  3x
[avision]   [30] 00000000b   0o   0d  0x
[avision]   [31] 00000000b   0o   0d  0x
[avision]   [32] 00000000b   0o   0d  0x
[avision]   [33] 00000000b   0o   0d  0x
[avision]   [34] 00000000b   0o   0d  0x
[avision]   [35] 00000000b   0o   0d  0x
[avision]   [36] 00000000b   0o   0d  0x
[avision]   [37] 00000000b   0o   0d  0x
[avision]   [38] 00000000b   0o   0d  0x
[avision]   [39] 00000000b   0o   0d  0x
[avision]   [40] 11111111b 377o 255d ffx
[avision]   [41] 00010100b  24o  20d 14x
[avision]   [42] 01100000b 140o  96d 60x
[avision]   [43] 11111111b 377o 255d ffx
[avision]   [44] 00000000b   0o   0d  0x
[avision]   [45] 00000111b   7o   7d  7x
[avision]   [46] 01101000b 150o 104d 68x
[avision]   [47] 00000100b   4o   4d  4x
[avision]   [48] 00011000b  30o  24d 18x
[avision]   [49] 00010000b  20o  16d 10x
[avision]   [50] 00000000b   0o   0d  0x
[avision]   [51] 00000000b   0o   0d  0x
[avision]   [52] 00000000b   0o   0d  0x
[avision]   [53] 00000000b   0o   0d  0x
[avision]   [54] 00000000b   0o   0d  0x
[avision]   [55] 00000000b   0o   0d  0x
[avision]   [56] 00000000b   0o   0d  0x
[avision]   [57] 00000000b   0o   0d  0x
[avision]   [58] 00000000b   0o   0d  0x
[avision]   [59] 00000000b   0o   0d  0x
[avision]   [60] 00000000b   0o   0d  0x
[avision]   [61] 00000000b   0o   0d  0x
[avision]   [62] 00000000b   0o   0d  0x
[avision]   [63] 00000000b   0o   0d  0x
[avision] set_window: [0]     window_id: 0
[avision] set_window: [2-3]   x-axis res: 75
[avision] set_window: [4-5]   y-axis res: 75
[avision] set_window: [6-9]   x-axis upper left: 0
[avision] set_window: [10-13] y-axis upper left: 0
[avision] set_window: [14-17] window width: 10113
[avision] set_window: [18-21] window length: 16769
[avision] set_window: [22]    brightness: 128
[avision] set_window: [23]    threshold: 128
[avision] set_window: [24]    contrast: 128
[avision] set_window: [25]    image composition: 5
[avision] set_window: [26]    bits per channel: 8
[avision] set_window: [27-28] halftone pattern: 0
[avision] set_window: [29]    padding_and_bitset: 3
[avision] set_window: [30-31] bit ordering: 0
[avision] set_window: [32]    compression type: 0
[avision] set_window: [33]    compression argument: 0
[avision] set_window: [34-35] paper length: 0
[avision] set_window: [40]    vendor id: ff
[avision] set_window: [41]    param lenght: 20
[avision] set_window: [42]    bitset1: 60
[avision] set_window: [43]    highlight: 255
[avision] set_window: [44]    shadow: 0
[avision] set_window: [45-46] line-width: 1896
[avision] set_window: [47-48] line-count: 1048
[avision] set_window: [49]    bitset2: 10
[avision] set_window: [50]    ir exposure time: 0
[avision] set_window: [51-52] r exposure: 0
[avision] set_window: [53-54] g exposure: 0
[avision] set_window: [55-56] b exposure: 0
[avision] set_window: [57]    bitset3: 0
[avision] set_window: [58]    auto focus: 0
[avision] set_window: [59]    line-width (MSB): 0
[avision] set_window: [60]    line-count (MSB): 0
[avision] set_window: [61]    background lines: 0
[avision] set_window: sending command. Bytes: 70
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] normal_calibration:
[avision] get_calib_format:
[avision] get_calib_format: read_data: 32 bytes
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] debug_print_calib_format:
[avision]   [0] 00000011b   3o   3d  3x
[avision]   [1] 01011000b 130o  88d 58x
[avision]   [2] 00000001b   1o   1d  1x
[avision]   [3] 00111111b  77o  63d 3fx
[avision]   [4] 00000001b   1o   1d  1x
[avision]   [5] 00000001b   1o   1d  1x
[avision]   [6] 00000101b   5o   5d  5x
[avision]   [7] 11110011b 363o 243d f3x
[avision]   [8] 01010001b 121o  81d 51x
[avision]   [9] 00000000b   0o   0d  0x
[avision]   [10] 11100000b 340o 224d e0x
[avision]   [11] 00000000b   0o   0d  0x
[avision]   [12] 11100000b 340o 224d e0x
[avision]   [13] 00000000b   0o   0d  0x
[avision]   [14] 11100000b 340o 224d e0x
[avision]   [15] 00000000b   0o   0d  0x
[avision]   [16] 00000000b   0o   0d  0x
[avision]   [17] 00000000b   0o   0d  0x
[avision]   [18] 00000000b   0o   0d  0x
[avision]   [19] 00000000b   0o   0d  0x
[avision]   [20] 00000000b   0o   0d  0x
[avision]   [21] 00000000b   0o   0d  0x
[avision]   [22] 10110000b 260o 176d b0x
[avision]   [23] 10001000b 210o 136d 88x
[avision]   [24] 10101101b 255o 173d adx
[avision]   [25] 10000001b 201o 129d 81x
[avision]   [26] 00000000b   0o   0d  0x
[avision]   [27] 00000000b   0o   0d  0x
[avision]   [28] 01000001b 101o  65d 41x
[avision]   [29] 10000001b 201o 129d 81x
[avision]   [30] 10000000b 200o 128d 80x
[avision]   [31] 10000000b 200o 128d 80x
[avision] get_calib_format: [0-1]  pixels per line: 856
[avision] get_calib_format: [2]    bytes per channel: 1
[avision] get_calib_format: [3]    line count: 63
[avision] get_calib_format: [4]    FLAG: MUST_DO_CALIBRATION
[avision] get_calib_format: [5]    Ability1: PACKED NEEDS_CALIB_TABLE_CHANNEL_BY_CHANNEL
[avision] get_calib_format: [6]    R gain: 5
[avision] get_calib_format: [7]    G gain: 243
[avision] get_calib_format: [8]    B gain: 81
[avision] get_calib_format: [9-10] R shading target: e0
[avision] get_calib_format: [11-12] G shading target: e0
[avision] get_calib_format: [13-14] B shading target: e0
[avision] get_calib_format: [15-16] R dark shading target: 0
[avision] get_calib_format: [17-18] G dark shading target: 0
[avision] get_calib_format: [19-20] B dark shading target: 0
[avision] get_calib_format: channels: 3
[avision] normal_calibration: using color calibration
[avision] get_calib_data: type 62, size 53928, chunk_size: 53928
[avision] get_calib_data: Reading 53928 bytes calibration data
[avision] Timeouts: write: 30000, read: 30000, status: 10000
[avision] avision_usb_status: timeout 10000, 1 retries
[avision] ==> (bulk read) going down ...
[avision] <== (bulk read) got: 1, status: 0
[avision] get_calib_data: Got 53928 bytes calibration data
[avision] sort_and_average:
[avision] sane_start: perform calibration failed: Out of memory
[avision] do_cancel:
Terminated

```

---

### Post by ecowan on 2009-06-03
Since four different 'front-end' scanner programs are all crashing x-windows, and sane-avision seems to be the common back-end, i did a little more digging. I found a suggestion on [www.sane-project.org/man/sane-avision.5.html](www.sane-project.org/man/sane-avision.5.html). So I tried ```
erny@mistry:~$ export SANE_DEBUG_AVISION=7
erny@mistry:~$ kooka
```
I attach the output it generated.
- Erny
or at least I tried to. I do have it in a file, if someone can can use it.

---

### Post by ecowan on 2009-06-03
So. I have a working scanner.
In launchpad I found a workaround.
I installed replaced libsane_1.0.19_1ubuntu3 with libsane_1.0.18-3ubuntu1_386.deb by 
'sudo dpkg -i --force-downgrade libsane....'

I also had to tweek /etc/udev/rules.d/45-libsane.rules.

So kooka, gscan2pdf and flegita are all working.

Ain't ubuntu great? - Erny

---

