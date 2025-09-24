# Overview

This project is a TikTok to Facebook Page video automation tool that automatically downloads videos from TikTok and posts them to Facebook Pages as Reels. The application extracts video information and URLs from TikTok links using web scraping techniques, downloads the video content, and then uploads it to Facebook using the Facebook Graph API. The tool is designed to streamline the process of content distribution across social media platforms.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Core Components

**Web Scraping Module**
- Uses regex patterns to extract video data from TikTok's client-side JavaScript
- Implements two fallback strategies for different TikTok page structures
- Maintains session cookies for proper request handling
- Problem solved: TikTok's dynamic content loading requires parsing embedded JSON data

**Video Download System**
- Downloads video content as binary blobs using extracted URLs
- Handles HTTP sessions and cookie management for authenticated requests
- Uses appropriate headers to mimic browser behavior
- Problem solved: TikTok requires proper browser simulation to access video files

**Facebook Integration Layer**
- Implements Facebook Graph API video upload workflow
- Supports chunked upload for large video files
- Handles upload session initialization and status monitoring
- Problem solved: Facebook requires specific upload protocols for video content

**Testing Framework**
- Validates library imports and function definitions
- Provides system health checks before execution
- Problem solved: Ensures all dependencies are properly configured

## Design Patterns

**Session Management**
- Uses Python requests.Session() for persistent HTTP connections
- Maintains cookies across requests for authentication
- Chosen for its simplicity and built-in cookie handling

**Error Handling Strategy**
- Implements fallback regex patterns for TikTok data extraction
- Uses try-catch blocks for graceful degradation
- Provides clear error messages in Vietnamese for user feedback

**Modular Function Design**
- Separates concerns between video extraction, download, and upload
- Each function handles a specific part of the workflow
- Enables easy testing and maintenance of individual components

# External Dependencies

## Required Python Libraries
- **requests**: HTTP client for web scraping and API calls
- **io**: Stream handling for video blob processing
- **time**: Timing controls for upload status polling
- **json**: JSON parsing for TikTok data extraction
- **re**: Regular expression matching for HTML parsing

## External Services
- **TikTok Platform**: Source for video content extraction
- **Facebook Graph API**: Target platform for video publishing
- **Facebook Pages API**: Specific endpoint for page content management

## Integration Points
- TikTok video URLs as input source
- Facebook Page access tokens for authentication
- Facebook Graph API endpoints for video upload workflow
- Browser user agents for proper web scraping behavior

The architecture prioritizes reliability through fallback mechanisms and clear separation of concerns, making it maintainable and extensible for future enhancements.