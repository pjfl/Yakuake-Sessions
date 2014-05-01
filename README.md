# Name

Yakuake::Sessions - Session Manager for the Yakuake Terminal Emulator

# Version

This documents version v0.13.$Rev: 0 $ of [Yakuake::Sessions](https://metacpan.org/pod/Yakuake::Sessions)

# Synopsis

    # To reduce typing define some shell aliases
    alias ys='yakuake_session'

    # Create some Yakuake sessions. Set each session to a different directory.
    # Run some commands in some of the sessions like an HTTP web development
    # server or tail -f on a log file. Set the tab titles for each session.
    # Now create a profile called dev
    ys create dev

    # Subsequently reload the dev profile
    ys load dev

    # Show the contents of the dev profile
    ys show dev

    # Edit the contents of the dev profile
    ys edit dev

    # Delete the dev profile
    ys delete dev

    # Command line help
    ys -? | -H | -h [sub-command] | list_methods | dump_self

# Description

Create, edit, load session profiles for the Yakuake Terminal Emulator. Sets
and manages the tab title text

# Configuration and Environment

Reads configuration from `~/.yakuakue_sessions/yakuake_session.json` which
might look like;

    {
       "doc_title": "Perl",
       "tab_title": "Oo.!.oO"
    }

See the [config class](https://metacpan.org/pod/Yakuake::Sessions::Config) for the full list of
configuration attributes

Defines the following list of attributes which can be set from the command
line;

- `config_dir`

    Directory containing the configuration files. Defaults to
    `~/.yakuake_sessions`

- `editor`

    The editor used to edit profiles. Can be set from the configuration
    file. Defaults to the environment variable `EDITOR` or if unset
    `emacs`

- `force`

    Overwrite the output file if it already exists

- `profile_dir`

    Directory to store the session profiles in

- `storage_class`

    File format used to store session data. Defaults to the config class
    value; `JSON`

Modifies these methods in the base class

- `run`

# Subroutines/Methods

## create

    yakuake_session create <profile_name>

Creates a new session profile in the `profile_dir`. Calls ["dump"](#dump)

## delete

    yakuake_session delete <profile_name>

Deletes the specified session profile

## dump

    yakuake_session dump <path>

Dumps the current sessions to file. For each tab it captures the
current working directory, the command being executed, the tab title text,
and which tab is currently active

## edit

    yakuake_session edit <profile_name>

Edit a session profile

## list

    yakuake_session list

List the session profiles stored in the `profile_dir`

## load

    yakuake_session load <profile_name>

Load the specified profile, recreating the tabs with their title text,
current working directories and executing commands

## select

    yakuakge_session select

Select the profile to load from the displayed list

## set\_tab\_title

    yakuake_session set_tab_title <title_text>

Sets the current tabs title text to the specified value. Defaults to the
vale supplied in the configuration

## set\_tab\_title\_for\_project

    yakuake_session set_tab_title_for_project <title_text>

Set the current tabs title text to the specified value. Must supply a
title text. Will save the project name for use by
`yakuake_session_tt_cd`

## show

    yakuake_session show <profile_name>

Display the contents of the specified session profile

# Diagnostics

Turning on debug, add `-D` to the command line, causes the session dump
and load subroutines to display the session tabs data

The `list_methods` command lists all of the callable the methods and
their abstracts

# Dependencies

- [Class::Usul](https://metacpan.org/pod/Class::Usul)
- [File::DataClass](https://metacpan.org/pod/File::DataClass)
- [Net::DBus](https://metacpan.org/pod/Net::DBus)

# Incompatibilities

None

# Bugs and Limitations

It is necessary to edit new session profiles and manually escape the shell
meta characters embeded in the executing commands

There are no known bugs in this module.Please report problems to
http://rt.cpan.org/NoAuth/Bugs.html?Dist=Yakuake-Sessions. Source code
is on Github git://github.com/pjfl/Yakuake-Sessions.git. Patches and
pull requests are welcome

# Acknowledgements

Larry Wall - For the Perl programming language

# Author

Peter Flanigan, `<pjfl@cpan.org>`

# License and Copyright

Copyright (c) 2014 Peter Flanigan. All rights reserved

This program is free software; you can redistribute it and/or modify it
under the same terms as Perl itself. See [perlartistic](https://metacpan.org/pod/perlartistic)

This program is distributed in the hope that it will be useful,
but WITHOUT WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE
