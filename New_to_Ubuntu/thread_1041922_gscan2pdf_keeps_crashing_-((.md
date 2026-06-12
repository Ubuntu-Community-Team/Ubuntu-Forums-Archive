---
title: "gscan2pdf keeps crashing :-(("
date: 2009-01-17
forum: New to Ubuntu
---

### Post by stinger30au on 2009-01-17
i have scanned in aobut 50 books with gscan2pdf and its worked well

now if i run it from shell i get this

gscan2pdf
Warning: Unrecognised image file format at /usr/bin/gscan2pdf line 1394.

Segmentation fault

gscan2pdf will start up. if i hit scan, the scanner runs, as soon as the scanner stops, gscan2pdf vansihes off screen and shell shows me the above eror

i tried doing a sudo synaptic and full removal and reinstall, but same thing

any ideas??

thanks

---

### Post by stinger30au on 2009-01-17
after some reading i found a debug option, hope this helps

gscan2pdf --debug
gscan2pdf 0.9.25
Using en_AU.UTF-8 locale
Gtk2-Perl version 1.183
Built for 2.13.3
Running with 2.14.4
Using GtkImageView version 1.6.1
Using Gtk2::ImageView version 0.04
$VAR1 = {
          'ocr panel' => '79',
          'no-blackfilter' => '',
          'frontend' => 'scanimage',
          'mode' => 'Gray',
          'output-pages' => '1',
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
          'unsharp radius' => '0',
          'window_maximize' => '',
          'no-border-scan' => '',
          'no-blurfilter' => '',
          'keywords' => '',
          'white-threshold' => '0.9',
          'y' => '297',
          'layout' => 'single',
          'unsharp amount' => '1',
          'cwd' => '/home/dez/Desktop/downloads',
          't' => '0',
          'OCR on scan' => '',
          'image type' => 'pdf',
          'Paper size' => 'A4',
          'Page range' => 'all',
          'subject' => '',
          'no-deskew' => '',
          'window_height' => '156',
          'startup warning' => '1',
          'rotate reverse' => '0',
          'brightness' => '0',
          'no-grayfilter' => '',
          'pages to scan' => '1',
          'resolution' => '200',
          'no-border-align' => '',
          'title' => 'test',
          'unpaper on scan' => '',
          'rotate facing' => '0',
          'cache options' => '1',
          'author' => '',
          'x' => '210',
          'calibration-cache' => 'no',
          'downsample dpi' => '150',
          'window_width' => '181',
          'threshold tool' => '80',
          'window_x' => '436',
          'deskew-scan-direction' => 'left,right',
          'quality' => '100',
          'window_y' => '99',
          'date offset' => '0',
          'unsharp sigma' => '1',
          'thumb panel' => '175',
          'version' => '0.9.25',
          'contrast' => '0',
          'scan prefix' => '',
          'unsharp threshold' => '0.05',
          'device' => 'plustek:libusb:001:008',
          'no-noisefilter' => '',
          'l' => '0',
          'SANE version' => 'scanimage (sane-backends) 1.0.19; backend version 1.0.19',
          'no-mask-scan' => '',
          'Page range default' => 'all',
          'downsample' => '',
          'restore window' => '',
          'black-threshold' => '0.33',
          'pdf compression' => 'png'
        };
Found PDF::API2
Found Image::Magick
Found ImageMagick
Found scanadf
Found xdg-email
Found gocr
Found tesseract
Found cjb2 (djvu)
Found unpaper
Found libtiff
Using /tmp/jOzI9AbCWA for temporary files
 scanimage --formatted-device-list="'%i','%d','%v %m'
" 2>/dev/null
Forked PID 8084
Waiting to reap process at /usr/bin/gscan2pdf line 3633.
Reaped PID -1
'0','plustek:libusb:001:004','Canon CanoScan N670U/N676U/LiDE20'
 scanimage --help --device-name='plustek:libusb:001:004'
Forked PID 8098
Waiting to reap process at /usr/bin/gscan2pdf line 4595.
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

Options specific to device `plustek:libusb:001:004':
  Scan Mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --depth 8|16bit [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --source Normal|Transparency|Negative [inactive]
        Selects the scan source (such as a document-feeder).
    --resolution 50..1200dpi [50]
        Sets the resolution of the scanned image.
    --preview[=(yes|no)] [no]
        Request a preview-quality scan.
  Geometry:
    -l 0..215mm [0]
        Top-left x position of scan area.
    -t 0..297mm [0]
        Top-left y position of scan area.
    -x 0..215mm [103]
        Width of scan-area.
    -y 0..297mm [76.21]
        Height of scan-area.
  Enhancement:
    --brightness -100..100% (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..100% (in steps of 1) [0]
        Controls the contrast of the acquired image.
    --custom-gamma[=(yes|no)] [no]
        Determines whether a builtin or a custom gamma-table should be used.
    --gamma-table 0..255,... [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..255,... [inactive]
        Gamma-correction table for the red band.
    --green-gamma-table 0..255,... [inactive]
        Gamma-correction table for the green band.
    --blue-gamma-table 0..255,... [inactive]
        Gamma-correction table for the blue band.
  Device-Settings:
    --lamp-switch[=(yes|no)] [no]
        Manually switching the lamp(s).
    --lampoff-time 0..999 (in steps of 1) [300]
        Lampoff-time in seconds.
    --lamp-off-at-exit[=(yes|no)] [yes]
        Turn off lamp when program exits
    --warmup-time -1..999 (in steps of 1) [inactive]
        Warmup-time in seconds.
    --lamp-off-during-dcal[=(yes|no)] [inactive]
        Always switches lamp off when doing dark calibration.
    --calibration-cache[=(yes|no)] [no]
        Enables or disables calibration data cache.
    --speedup-switch[=(yes|no)] [inactive]
        Enables or disables speeding up sensor movement.
    --calibrate [inactive]
        Performs calibration
  Analog frontend:
    --red-gain -1..63 (in steps of 1) [-1]
        Red gain value of the AFE
    --green-gain -1..63 (in steps of 1) [-1]
        Green gain value of the AFE
    --blue-gain -1..63 (in steps of 1) [-1]
        Blue gain value of the AFE
    --red-offset -1..63 (in steps of 1) [-1]
        Red offset value of the AFE
    --green-offset -1..63 (in steps of 1) [-1]
        Green offset value of the AFE
    --blue-offset -1..63 (in steps of 1) [-1]
        Blue offset value of the AFE
    --redlamp-off -1..16363 (in steps of 1) [-1]
        Defines red lamp off parameter
    --greenlamp-off -1..16363 (in steps of 1) [-1]
        Defines green lamp off parameter
    --bluelamp-off -1..16363 (in steps of 1) [-1]
        Defines blue lamp off parameter
  Buttons:

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    plustek:libusb:001:004
$VAR1 = {
          'gamma-table' => {
                             'tip' => 'Gamma-correction table.  In color mode this option equally affects the red, green, and blue channels simultaneously (i.e., it is an intensity gamma table).',
                             'min' => '0',
                             'max' => '255',
                             'default' => 'inactive'
                           },
          'redlamp-off' => {
                             'tip' => 'Defines red lamp off parameter',
                             'step' => '1',
                             'min' => '-1',
                             'max' => '16363',
                             'default' => '-1'
                           },
          'mode' => {
                      'tip' => 'Selects the scan mode (e.g., lineart, monochrome, or color).',
                      'default' => 'Color',
                      'values' => [
                                    'Lineart',
                                    'Gray',
                                    'Color'
                                  ]
                    },
          'y' => {
                   'tip' => 'Height of scan-area.',
                   'min' => '0',
                   'max' => '297',
                   'default' => '76.21'
                 },
          'green-gain' => {
                            'tip' => 'Green gain value of the AFE',
                            'step' => '1',
                            'min' => '-1',
                            'max' => '63',
                            'default' => '-1'
                          },
          't' => {
                   'tip' => 'Top-left y position of scan area.',
                   'min' => '0',
                   'max' => '297',
                   'default' => '0'
                 },
          'greenlamp-off' => {
                               'tip' => 'Defines green lamp off parameter',
                               'step' => '1',
                               'min' => '-1',
                               'max' => '16363',
                               'default' => '-1'
                             },
          'depth' => {
                       'tip' => 'Number of bits per sample, typical values are 1 for "line-art" and 8 for multibit scans.',
                       'default' => '8',
                       'values' => [
                                     '8',
                                     '16bit'
                                   ]
                     },
          'blue-gain' => {
                           'tip' => 'Blue gain value of the AFE',
                           'step' => '1',
                           'min' => '-1',
                           'max' => '63',
                           'default' => '-1'
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
          'resolution' => {
                            'tip' => 'Sets the resolution of the scanned image.',
                            'min' => '50',
                            'max' => '1200',
                            'default' => '50'
                          },
          'source' => {
                        'tip' => 'Selects the scan source (such as a document-feeder).',
                        'default' => 'inactive',
                        'values' => [
                                      'Normal',
                                      'Transparency',
                                      'Negative'
                                    ]
                      },
          'lamp-switch' => {
                             'tip' => 'Manually switching the lamp(s).',
                             'default' => 'no',
                             'values' => [
                                           'yes',
                                           'no'
                                         ]
                           },
          'blue-offset' => {
                             'tip' => 'Blue offset value of the AFE',
                             'step' => '1',
                             'min' => '-1',
                             'max' => '63',
                             'default' => '-1'
                           },
          'red-gamma-table' => {
                                 'tip' => 'Gamma-correction table for the red band.',
                                 'min' => '0',
                                 'max' => '255',
                                 'default' => 'inactive'
                               },
          'green-gamma-table' => {
                                   'tip' => 'Gamma-correction table for the green band.',
                                   'min' => '0',
                                   'max' => '255',
                                   'default' => 'inactive'
                                 },
          'x' => {
                   'tip' => 'Width of scan-area.',
                   'min' => '0',
                   'max' => '215',
                   'default' => '103'
                 },
          'custom-gamma' => {
                              'tip' => 'Determines whether a builtin or a custom gamma-table should be used.',
                              'default' => 'no',
                              'values' => [
                                            'yes',
                                            'no'
                                          ]
                            },
          'calibration-cache' => {
                                   'tip' => 'Enables or disables calibration data cache.',
                                   'default' => 'no',
                                   'values' => [
                                                 'yes',
                                                 'no'
                                               ]
                                 },
          'blue-gamma-table' => {
                                  'tip' => 'Gamma-correction table for the blue band.',
                                  'min' => '0',
                                  'max' => '255',
                                  'default' => 'inactive'
                                },
          'red-gain' => {
                          'tip' => 'Red gain value of the AFE',
                          'step' => '1',
                          'min' => '-1',
                          'max' => '63',
                          'default' => '-1'
                        },
          'bluelamp-off' => {
                              'tip' => 'Defines blue lamp off parameter',
                              'step' => '1',
                              'min' => '-1',
                              'max' => '16363',
                              'default' => '-1'
                            },
          'contrast' => {
                          'tip' => 'Controls the contrast of the acquired image.',
                          'step' => '1',
                          'min' => '-100',
                          'max' => '100',
                          'default' => '0'
                        },
          'speedup-switch' => {
                                'tip' => 'Enables or disables speeding up sensor movement.',
                                'default' => 'inactive',
                                'values' => [
                                              'yes',
                                              'no'
                                            ]
                              },
          'warmup-time' => {
                             'tip' => 'Warmup-time in seconds.',
                             'step' => '1',
                             'min' => '-1',
                             'max' => '999',
                             'default' => 'inactive'
                           },
          'lamp-off-during-dcal' => {
                                      'tip' => 'Always switches lamp off when doing dark calibration.',
                                      'default' => 'inactive',
                                      'values' => [
                                                    'yes',
                                                    'no'
                                                  ]
                                    },
          'red-offset' => {
                            'tip' => 'Red offset value of the AFE',
                            'step' => '1',
                            'min' => '-1',
                            'max' => '63',
                            'default' => '-1'
                          },
          'lamp-off-at-exit' => {
                                  'tip' => 'Turn off lamp when program exits',
                                  'default' => 'yes',
                                  'values' => [
                                                'yes',
                                                'no'
                                              ]
                                },
          'l' => {
                   'tip' => 'Top-left x position of scan area.',
                   'min' => '0',
                   'max' => '215',
                   'default' => '0'
                 },
          'calibrate' => {
                           'tip' => 'Performs calibration',
                           'default' => 'inactive'
                         },
          'green-offset' => {
                              'tip' => 'Green offset value of the AFE',
                              'step' => '1',
                              'min' => '-1',
                              'max' => '63',
                              'default' => '-1'
                            },
          'lampoff-time' => {
                              'tip' => 'Lampoff-time in seconds.',
                              'step' => '1',
                              'min' => '0',
                              'max' => '999',
                              'default' => '300'
                            }
        };
$VAR1 = [];
$VAR1 = {
          'mode' => 'Color',
          'contrast' => '0',
          'x' => '210',
          'calibration-cache' => 'no',
          'y' => '297',
          'l' => '0',
          'brightness' => '0',
          'resolution' => '350',
          't' => '0'
        };
rotate facing 0
rotate reverse 0
unpaper 
OCR 
 scanimage --device-name='plustek:libusb:001:004' --mode='Color' --contrast='0' -x 210 --calibration-cache='no' -y 297 -l 0 --brightness='0' --resolution='350' -t 0 --batch --progress --batch-count=1
Forked PID 8125
Scanning 1 pages, incrementing by 1, numbering from 1
Scanning page 1
Scanned page 1. (scanner status = 5)
Importing out1.pnm, format Portable anymap
Added /tmp/jOzI9AbCWA/P98uAEr0w5.pnm at page 1 with resolution 350
Warning: Unrecognised image file format at /usr/bin/gscan2pdf line 1394.

Segmentation fault

---

### Post by stinger30au on 2009-01-17
Fixxed it!!!
 

yee-haw!!!!

after *MUCH* reading and searching, i found if i start up shell and type this


 sudo rm -rf ~/.gscan2pdf


it works again


YIPPIE!!!

---

### Post by zipher on 2009-02-14
Hi Stinger30au,

Glad that you've finally solved your prob there, hope things are going OK.

The reason I found your thread, is because I was looking for stuff to do with image enhancement, scanning and so on.

The motivation to reply is really to ask how you stumbled upon the idea (if stumble upon it you did) of deleting files with those parameters as a fix, and why you tried it at all, given the cautionary notes at the bottom of your posts.

Not that I'm being critical, simply bemused as well as interested... allow me to expand:
I have often tried to 'solve' problems on my computer by deleting files, partitions and so on, and persist in thinking that this is a quite logical approach even though it has never or almost never, actually worked. Not only can I not explain where I conceived the notion that it might work, but also, I can relate that most recently whilst attempting to pimp up my partition schema, I nearly lost everything!:lolflag:
Hence my interest in a deletion fix that actually worked, and interest in following it up!
I have since learned that when deleting files, other files with 'hooks' need to be updated in order to avoid meltdown.

Anyway, if you're still with me, I wonder if I could pass one more by you?
I'm trying to scan a job application form and improve the quality of the image without actually changing it. Any ideas how this could be achieved pls?

Thanks - Jon zipher Lamb:)

---

### Post by stinger30au on 2009-02-15
i found another thread and they had problems that was different to mine, so i thought what the hell i will delete the directory like they said and see what happens

lucky for me it worked

with scanning the job form, im not sure i follow you eactly, but if it is a blank and white form, i would scan it in using "lineart" at no less then 400 dpi

hope this helps

---

