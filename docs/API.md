# API Documentation

## Installation

```bash
npm install @skillforge/github-automation
```

## Quick Start

```typescript
import { createGitHubSkill, SkillConfigBuilder } from '@skillforge/github-automation';

const config = new SkillConfigBuilder()
  .setGitHubToken('ghp_your_token')
  .setLicenseKey('SF-GH-XXXX-XXXX-XXXX')
  .build();

const skill = createGitHubSkill();
await skill.initialize(config);
```

## Actions

### Issue Automation

#### Create Issue
```typescript
await skill.execute({
  action: 'issue.create',
  params: {
    title: 'Bug Report',
    body: 'Description...',
    labels: ['bug'],
    assignees: ['developer']
  }
});
```

#### List Issues
```typescript
await skill.execute({
  action: 'issue.list',
  params: {
    state: 'open',
    labels: ['bug']
  }
});
```

### PR Analysis

#### Analyze PR
```typescript
const analysis = await skill.execute({
  action: 'pr.analyze',
  params: {
    pullNumber: 42
  }
});
```

### Release Automation

#### Create Release
```typescript
await skill.execute({
  action: 'release.create',
  params: {
    tagName: 'v1.0.0',
    generateReleaseNotes: true
  }
});
```

## Configuration

### SkillConfigBuilder

| Method | Description |
|--------|-------------|
| `setGitHubToken(token)` | Set GitHub personal access token |
| `setLicenseKey(key)` | Set your license key |
| `setDefaultOwner(owner)` | Set default repository owner |
| `setDefaultRepo(repo)` | Set default repository name |
| `enableAllFeatures()` | Enable all available features |

## License Tiers

| Feature | Lite | Pro | Enterprise |
|---------|:----:|:---:|:----------:|
| Issue Automation | ✅ | ✅ | ✅ |
| PR Analysis | Basic | Full | Full |
| Release Automation | ❌ | ✅ | ✅ |
| Multi-Repo | ❌ | ❌ | ✅ |
| Custom Rules | ❌ | ❌ | ✅ |
