SimpleAudioSplitter
===================
SimpleAudioSplitter is an audio splitter for Linux.

TODO
----
- [ ] Add a json parser;
- [ ] Add gmock and gtest;
- [x] Model the split configuration file;
- [ ] Implement JsonParser, a class that read/write json files;
- [ ] Implement SplitMark, a class that holds the beginning, ending and name of the split;
- [ ] Implement AudioReader, a class that read audio files;
- [ ] Implement AudioWriter, a class that write (duh!) audio files;
- [ ] Implement AudioSplitter, a class that will split a loaded audio into small pieces based on the SplitMark config;

Split configuration file model:
-------------------------------
```json
{
    "00:00": "part1",
    "00:30": "part2",
    "30:00": "part3",
    "120:00": "part4"
}

```

- part1 will cut the audio from time 00:00 until 00:30;
- part2 will cut the audio from time 00:30 until 30:00;
- part3 will cut the audio from time 30:00 until 120:00;
- part4 will cut the audio from time 120:00 until the end of the audio;

I'm thinking in a way for the user to ignore some parts of the audio file, for
example, the user don't want the audio from time 37:00 until 89:00 in part3, in
the actual model, he will need to create a new split mark and than join part3_1
(30:00 - 37:00) with part3_2 (89:00 - 120:00) to accomplish this, it will also
create an unwanted audio file for part3_garbage (37:00 - 89:00).

License
-------
This software is licensed under the terms of GNU GPL v3, read "LICENSE" for
more info.
