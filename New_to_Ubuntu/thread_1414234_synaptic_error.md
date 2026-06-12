---
title: "synaptic error"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by DarkestStar on 2010-02-23
Have just installed Karmic Koala and opened up synaptic and now have this error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Ran this terminal line to correct the problem and saw this:

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

Typed dpkg --help in and saw this:

Commands:
  -i|--install       <.deb file name> ... | -R|--recursive <directory> ...
  --unpack           <.deb file name> ... | -R|--recursive <directory> ...
  -A|--record-avail  <.deb file name> ... | -R|--recursive <directory> ...
  --configure        <package> ... | -a|--pending
  --triggers-only    <package> ... | -a|--pending
  -r|--remove        <package> ... | -a|--pending
  -P|--purge         <package> ... | -a|--pending
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.
  --update-avail <Packages-file>   Replace available packages info.
  --merge-avail <Packages-file>    Merge with info from file.
  --clear-avail                    Erase existing available info.
  --forget-old-unavail             Forget uninstalled unavailable pkgs.
  -s|--status <package> ...        Display package status details.
  -p|--print-avail <package> ...   Display available version details.
  -L|--listfiles <package> ...     List files `owned' by package(s).
  -l|--list [<pattern> ...]        List packages concisely.
  -S|--search <pattern> ...        Find package(s) owning file(s).
  -C|--audit                       Check for broken package(s).
  --print-architecture             Print dpkg architecture.
  --compare-versions <a> <op> <b>  Compare version numbers - see below.
  --force-help                     Show help on forcing.
  -Dh|--debug=help                 Show help on debugging.

  -h|--help                        Show this help message.
  --version                        Show the version.
  --license|--licence              Show the copyright licensing terms.

Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help).

For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep.

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --[no-]triggers            Skip or force consequential trigger processing.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>,...
                             Ignore dependencies involving <package>.
  --force-...                Override problems (see --force-help).
  --no-force-...|--refuse-...
                             Stop when problems encountered.
  --abort-after <n>          Abort after encountering <n> errors.

Comparison operators for --compare-versions are:
  lt le eq ne ge gt       (treat empty version as earlier than any version);
  lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
  < << <= = >= >> >       (only for compatibility with control file syntax).

Use `dselect' or `aptitude' for user-friendly package management.


How do I get Synaptic to function?

---

### Post by DarkestStar on 2010-02-23
Have just attemped to run Synaptic again and worked so no help needed currently
thanks for looking

---

