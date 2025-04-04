# Mopidy Spotify Render

[Mopidy](https://mopidy.com/) extension for playing music from [Spotify](https://www.spotify.com/).

Mopidy-Spotify-Render:
Created compiling librespot for Raspberry Pi (Ported from Moode)

- Working support for the following features is currently available:
- Works directly with alsa
- When Spotify Renderer is connected the current playing from other source is stopped
- Current Playing shows track information
- Seek Position only updates on playing, pause & seek actions on spotify app.



## Dependencies

- A Spotify Premium subscription. Mopidy-Spotify **will not** work with Spotify
  Free, just Spotify Premium.

- Mopidy >= 3.4. The music server that Mopidy-Spotify extends.

Verify the GStreamer spotify plugin is correctly installed:

```sh
gst-inspect-1.0 spotifyaudiosrc | grep Version | awk '{print $2}'
```

## Installation & development environment

Install by running:
```sh
git clone https://github.com/varungujjar/mopidy-spotify-render/
cd mopidy-spotify-render
pip install -e .
```
Add the following lines to core.playback.py within the PlaybackController class
```sh
    def set_metadata(self, track: TlTrack) -> None:
        """
        Set Track meta data seperately.
        """
        self._set_current_tl_track(track)

    def set_position(self, position: DurationMs) -> None:
        """
        Set Track position seperately.
        """
        self._pending_position = position
```

## Configuration

Before starting Mopidy, you must visit https://mopidy.com/ext/spotify/#authentication
to authorize this extension against your Spotify account:

```ini
[spotify]
client_id = ... client_id value you got from mopidy.com ...
client_secret = ... client_secret value you got from mopidy.com ...
```
## Project resources
- [Configuration Options ](https://github.com/librespot-org/librespot/wiki/Options)
- [Source code](https://github.com/mopidy/mopidy-spotify](https://github.com/varungujjar/mopidy-spotify-render/)

