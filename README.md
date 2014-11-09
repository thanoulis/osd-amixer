osd-amixer
==========
osd-amixer is a Perl program which uses amixer and xosd to change system sound volume.

osd-amixer is meant to run as a background process, continuously reading from its named pipe (fifo) for specific keywords/commands. This way it can easily be used in any desktop environment or window manager using shell commands, shell scripts, keyboard shortcuts or even mouse gestures.

For more information: `perldoc osd-mixer`

KEYWORDS
--------
* up
    raise volume by 3%.

* down
    lower volume by 3%.

* toggle
    toggle mute status on/off.

* exit
    stop running osd-amixer and close its named pipe.

ENVIRONMENT
-----------
  OSD_AMIXER
    osd-amixer uses the environment variable OSD_AMIXER to create a named pipe
    (fifo) and read from it. If this variable is missing,
    $HOME/.osd-amixer.fifo is used instead.

EXAMPLES
--------
  Command line:
  ```shell
        echo up > ~/.osd-amixer.fifo
        echo toggle > ~/.osd-amixer.fifo
  ```
  Bash script:
  ```shell
        #!/bin/bash
        osd_fifo=${OSD_AMIXER:-"$HOME/.osd-amixer.fifo"}
        [[ -p $osd_fifo ]] && echo $1 > $osd_fifo
  ```

DEPENDENCIES
------------
  Perl
    version 5.10 or later.

  IPC::Run
    version 0.90 or later.

  X::Osd
    version 0.7.0 or later.

  alsa-utils
    version 1.0.0 or later.
