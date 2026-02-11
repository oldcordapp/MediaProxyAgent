# MediaProxyAgent
A simple, efficient agent designed to extend Oldcord's WebRTC voice capabilities across multiple geographic regions. <br>
The **Media Proxy Agent** acts as a server for Oldcord to connect to, enabling you to deploy media servers dedicated solely to voice traffic in different locations (e.g., US-East, EU-Central). This improves latency and quality for users worldwide. <br>

# Features
  - **Regional Voice Deployment**: Easily scale your instance's voice capabilities.
  - **Automatic IP Discovery**: Reports the server's public address (IP/Port) to the Signaling Server for seamless WebRTC connection handling (NAT Traversal).
  - **Efficient Event Forwarding**: Batches and relays real-time events (like speaking_events) from the media server back to the Signaling Server.

# Setup
Before using, please make sure your Oldcord instance has `mr_server` -> `enabled` (set to `true`) in the configuration.

1. **Prerequisites** <br>
     You need `Node.js` and `npm` installed on your target voice server.

3. **Installation** <br>
  Clone this repository and install dependencies:
  ```bash
    git clone https://github.com/oldcordapp/MediaProxyAgent
    cd MediaProxyAgent
    npm install
  ```

3. **Run the agent** <br>
    Start the agent on your target server, passing the port and the public IP exposure flag.
    Argument | Summary | Example
    --- | --- | --- |
    [PORT] | Set the port for the server to listen on | 4444
    [PUBLIC_IP_FLAG] | Set to true to use the server's public IP address (Recommended for production) or false to use a local IP address | true
    
    Example usage: `node server.js 4444 true`

4. **Profit** <br>
    Oldcord will connect to the server, exchange connection information for future clients, wait for instructions from the Signaling Server to manage voice rooms and manage the actual webrtc voice traffic by itself. <br>
    Now go join some voice calls (Provided you're using 2017 or 2018 client builds and Chromium) and have fun!
